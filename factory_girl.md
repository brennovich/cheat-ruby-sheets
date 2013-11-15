## Defining factories

```ruby
FactoryGirl.define do

  # Default 
  # It will use the User class
  factory :user do
    first_name "John"
    last_name  "Doe"
    admin false
  end

  # Specifying the class 
  # It will use the User class, instead of Admin class
  factory :admin, class: User do
    first_name "Admin"
    last_name  "User"
    admin      true
  end

end
```

## Building factories

```ruby
# Returns an User instace that's not saved
user = FactoryGirl.build(:user)

# Returns a saved User instance
user = FactoryGirl.create(:user)

# Returns a hash f attributes that can be used to build an User instance
attrs = FactoryGirl.attributes_for(:user)

# Returns an object with all defined attributes stubbed out
stub = FactoryGirl.build_stubbed(:user)

# Passing a block to any of the methods above will yield the return object
FactoryGirl.create(:user) do |user|
  user.posts.create(attributes_for(:post))
end

# Overriding attributes of a factory
user = FactoryGirl.build(:user, first_name: "Joe")
user.first_name
# => "Joe"

# No matter which build strategy is used to override attributes
user = FactoryGirl.create(:user, first_name: "Joe")
user.first_name
# => "Joe"
```

## Aliases