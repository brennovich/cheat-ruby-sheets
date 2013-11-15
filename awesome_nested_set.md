## Awesome Nested Set

### Setup

To make use of `awesome_nested_set`, your model needs to have 3 fields:
`lft`, `rgt`, and `parent_id`. The names of these fields are configurable:

```ruby
class CreateCategories < ActiveRecord::Migration
  def self.up
    create_table :categories do |t|
      t.string :name
      t.integer :parent_id
      t.integer :lft
      t.integer :rgt
    end
  end

  def self.down
    drop_table :categories
  end
end
```

Enable the nested set functionality by declaring `acts_as_nested_set` on your model

```ruby
class Category < ActiveRecord::Base
  acts_as_nested_set
end
```

### Basic Usage

Create a root node:

```ruby
science = Category.create! name: 'Science'
```

Put a new thing inside this root node:

```ruby
physics = Category.create! name: 'Physics'
physics.move_to_child_of science
```

Put another thing inside the 'physics' node:

```ruby
gravity = Category.create! :name: 'Classical Mechanics'
gravity.move_to_child_of physics
```

Reload the root node:

```ruby
science.reload
```

Now you should have something that resembles this:

```text
Science
'-- Physics
    '-- Classical Mechanics
```

### Callbacks

Handful `ActiveRecord` callbacks, when moving a node:

```ruby
before_move
after_move
around_move
```

### Hooks

You can pass hooks to the `acts_as_nested_set` macro:

```ruby
acts_as_nested_set before_add: :do_before_add_stuff,
                   after_add: :do_after_add_stuff,
                   before_remove: :do_before_remove_stuff,
                   after_remove: :do_after_remove_stuff
```

### Methods

There are cool methods to help you walk through your nested set. Grabbing `roots`:

```ruby
Category.root # The first root node
Category.roots # All root nodes
```

Accessing tree levels without touching DB:

```ruby
Category.each_with_level(Category.root.self_and_descendants) do |category, level|
  # My fancy code
end
```

Node navigation (touchs DB):

```ruby
category.root # Root for this node
category.level # The level of this object in the tree (e.g. root = 0)
category.parent # The node's immediate parent
category.children # Array of immediate children (just those in the next level)
category.ancestors # Array of all parents, parents' parents, etc, excluding self
category.self_and_ancestors # Array of all parents, parents' parents, etc, including self
category.siblings # Array of brothers and sisters (all at that level), excluding self
category.self_and_siblings # Array of brothers and sisters (all at that level), including self
category.descendants # Array of all children, children's children, etc., excluding self
category.self_and_descendants # Array of all children, children's children, etc., including self
category.leaves # Array of all descendants that have no children
```

Node navigation (without touching DB):

```ruby
category.root? # Returns true if this is a root node
category.child? # Returns true if this is a child node (i.e. it has a parent)
category.is_ancestor_of?(obj) # Returns true if nested by any obj
category.is_or_is_ancestor_of?(obj) # Returns true if nested by any obj or self is obj
category.is_descendant_of?(obj) # Returns true if self is nested under obj
category.is_or_is_descendant_of?(obj) # Returns true if self is nested under obj or self is obj
category.leaf? # Returns true if this is a leaf node (i.e. it has no children)
```
