# Cheat Ruby Sheets

One cheat sheet repo to rule them all.

## Collaborating

1. Fork
2. Create a feature-branch with the name of the thing that you are cheating
3. Follow the style conventions below
4. Pull Request

### Naming pattern

`gem_name.md` - Name of the cheatsheet for that gem. `gem_name` should be exactly
equals to the gem name in [Rubygems](http://rubygems.org/).

### Styles

Start your headings with `##` instead `#`:

**Right:**

## Styleguide

**Wrong:**

# Styleguide

When showing code describe the following line with comments:

```ruby
# Execute the given script, not returning a result. This is useful for scripts that return
# complex objects, such as jQuery statements. +execute_script+ should be used over
# +evaluate_script+ whenever possible.
page.execute_script("$('#change').text('Funky Doodle')")
```

If you wants to show the return of the current line, add `# =>` bellow of the code:

```ruby
page.evaluate_script("1+3")
# => 4
```

Respect the code indentation:


**Right:**

```ruby
within(search_form) do
  fill_in 'Name', with: 'iOS 7'
  click_button 'Search'
end
```

**Wrong:**

```ruby
    within(search_form) do
      fill_in 'Name', with: 'iOS 7'
      click_button 'Search'
    end
```

### To Do

- More, more and more cheat sheets
- Cool script to generate beautiful `.pdf` version of the `.md` versions
