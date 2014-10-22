# Rake Tasks

## Simple task
 *Code*
```ruby
desck "Says to you a Hello World"
task :hello_world do
  puts "Hello world"
end

```
 *Console call*
```console
rake hello_world
```

## Task with arguments
 *Code*
```ruby
desc "Create a default user as admin"
task :create_user, [:email, :password] do |t, args|
  args.email # => email argument
  args.password # => password argument
end
```

 *Console call*
```console
rake create_user[example@example.com,mypassword]
```

## Tasks with dependencies
```ruby
task :environment do
  puts "loading environment!"
end
...
desc "This task loads another task"
task :create_user => :environment do
  puts "This task will execute task environment before"
end
```
