## Capybara Actions

```ruby
# Anchor
click_link 'Save'

# Button
click_button 'awesome'

# Both above
click_link_or_button 'Save'

# Text (area) field
fill_in 'Name', with: 'Content'

# Checkbox
check 'Content'
uncheck 'Content'

# Radio button
choose 'Content'

# Select option from select tag
select 'Option', from: 'Label'

# File input
attach_file Rails.root.join('spec/fixture/some_file.png')

# Drag and drop
draggable_element = find('.drag-me')
droppable_element = find('.drop-here')
draggable_element.drag_to(droppable_element)
```

## Capybara Finders

```ruby
page.all(:xpath, '//a')

page.first(:xpath, '//a')

page.find('//textarea[@id="additional_newline"]')

page.find(:xpath, "//input[@id='form_pets_dog']")['checked']
# => true

page.find(:css, '#with_focus_event').trigger(:focus)

page.find(:css,'.wrapper').hover

page.find_field("test_field").value
# => 'blah'

page.find_by_id('red').tag_name
# => 'a'

# finds invisible elements when false
page.find_by_id("hidden_via_ancestor", visible: false)

page.find_button('What an Awesome')[:value]
# => 'awesome'

page.find_link('abo').text
# => 'labore'

page.find_link('other')[:href]
# => '/some_uri'
```

**Note:** `find` will wait for an element to appear on the page, as explained in the Ajax section. If the element does not appear it will raise an error.

**Note:** In XPath the expression `//` means something very specific, and it might not be what you think. Contrary to common belief, `//` means "anywhere in the document" not "anywhere in the current context".


## Capybara Scoped Finder `within`

```ruby
within(search_form) do
  fill_in 'Name', with: 'iOS 7'
  click_button 'Search'
end

def search_form
  '.search_form'
end

within_fieldset("villain_fieldset") do
  # ...
end

within_table("some_table") do
  # ...
end

# Execute the given block within the given iframe using given frame name or index.
#
within_frame('some_frame') do
end

save_page

# You need to install launchy gem.
save_and_open_page
```

## Capybara Common

```ruby
visit("http://google.com")

page.current_url
page.title

# Execute the given script, not returning a result. This is useful for scripts that return
# complex objects, such as jQuery statements. +execute_script+ should be used over
# +evaluate_script+ whenever possible.
page.execute_script("$('#change').text('Funky Doodle')")

# Evaluate the given JavaScript and return the result. Be careful when using this with
# scripts that return complex objects, such as jQuery statements. +execute_script+ might
# be a better alternative.
page.evaluate_script("1+3")
# => 4

using_wait_time 6 do
  # ... Changed Capybara.default_wait_time in this block scope.
end
```

## Capybara Matchers

```ruby
expect(page).to have_content("Some Content")
expect(page).to have_no_content("Some Content")

# True if there is a anchor tag with text matching regex
expect(page).to have_xpath("//a")
expect(page).to have_xpath("//a",:href => "google.com")
expect(page).to have_xpath("//a[@href => 'google.com']")
expect(page).to have_xpath("//a[contains(.,'some string')]")
expect(page).to have_xpath("//p//a", :text => /re[dab]i/i, :count => 1)

# Can take both xpath and css as input and can take arguments similar to both have_css and have_xpath
expect(page).to have_selector(:xpath, "//p/h1")
expect(page).to have_selector(:css, "p a#post_edit_path")

expect(page).to have_css("input#post_title")
expect(page).to have_css("input#post_title", :value => "Capybara cheatsheet")

# True if there are 3 input tags in response
expect(page).to have_css("input", :count => 3)

# True if there or fewer or equal to 3 input tags
expect(page).to have_css("input", :maximum => 3)

# True if there are minimum of 3 input tags
expect(page).to have_css("input", :minimum => 3)

# True if there 1 to 3 input tags
expect(page).to have_css("input", :between => 1..3)

# True if there is a anchor tag with text hello
expect(page).to have_css("p a", :text => "hello")
expect(page).to have_css("p a", :text => /[hH]ello(.+)/i)

# For making capybara to take css as default selector
Capybara.default_selector = :css

# Checks for the presence of the input tag
expect(page).to have_selector("input")

# Checks for input tag with value
expect(page).to have_selector("input", :value =>"Post Title")

expect(page).to have_no_selector("input")

# For making capybara to take css as default selector
Capybara.default_selector = :xpath

# Checks for the presence of the input tag
expect(page).to have_selector("//input")

# Checks for input tag with value
expect(page).to have_selector("//input", :value =>"Post Title")

# Checks for presence of a input field named FirstName in a form
expect(page).to have_field("FirstName")
expect(page).to have_field("FirstName", :value => "Rambo")
expect(page).to have_field("FirstName", :with => "Rambo")

expect(page).to have_link("Foo")
expect(page).to have_link("Foo", :href=>"googl.com")
expect(page).to have_no_link("Foo", :href=>"google.com")
```

## Capybara setup

```ruby
Capybara.configure do |config|
  # The default host to use when giving a relative URL to visit
  config.app_host = 'http://www.google.com'

  # Where dynamic assets are hosted - will be prepended to relative asset locations if present (Default: nil)
  config.asset_host = nil

  # Whether the Rack server's port should automatically be inserted into every visited URL
  config.always_include_port = false

  # Whether to start a Rack server for the given Rack app (Default: true)
  config.run_server = true

  # Methods which take a selector use the given type by default. (Can be :css or :xpath, DEFAULT CSS).
  config.default_selector = :css

  # The number of seconds to wait for asynchronous processes to finish (Default: 2)
  config.default_wait_time = 2

  # Whether to ignore hidden elements on the page (Default: true)
  config.ignore_hidden_elements = true

  config.default_host = 'http://www.example.com'

  # Whether to automatically reload elements as Capybara is waiting (Default: true)
  config.automatic_reload = true

  # Can be :first, :smart, :prefer_exact or :one.
  config.match = :smart

  # Can specify whether to match substrings or entire text. (Default: false)
  config.exact = false

  # Ignores server errors if false.
  config.raise_server_errors = false

  # Will ignores invisible text
  # But you can search invisible texts with :all option: 'page.find(:id, "hidden-text").text(:all)'
  config.visible_text_only = true

  # Where to put pages saved through save_and_open_page (Default: Dir.pwd)
  config.save_and_open_page_path = Dir.pwd

  # The name of the driver to use by default. (Default: :rack_test)
  config.default_driver = :rack_test

  # The name of a driver to use for JavaScript enabled tests. (Default: :selenium)
  config.javascript_driver = :selenium
end
```

## Register drivers

You can register drivers to test against other browsers:

```ruby
Capybara.register_driver :selenium_chrome do |app|
  Capybara::Selenium::Driver.new(app, :browser => :chrome)
end

Capybara.register_driver :selenium_firefox do |app|
  Capybara::Selenium::Driver.new(app, :browser => :firefox)
end

Capybara.register_driver :selenium_safari do |app|
  Capybara::Selenium::Driver.new(app, :browser => :safari)
end
```

They you can use configuring the default_driver:

```ruby
Capybara.configure do |config|
  config.default_driver = :selenium_safari
end
```

## Collaborators

1. @tomas-stefano
2. @brennovich
3. @carloslopes
