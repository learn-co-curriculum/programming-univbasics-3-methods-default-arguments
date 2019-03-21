# Title

## Learning Goals

- Define a method with optional arguments
- Define a method with optional and required arguments

## Introduction

If we revisit the coffee shop scenario, typically a name may be given when you
place your order so that your name can be called when the order is ready. What
happens when they don't ask for a name? Usually, they _default_ to calling out
the order that was placed. This may not be as personalized to you, but it's
better than not knowing when your order is ready!

In Ruby, we've seen that when a method accepts arguments, those arguments become
required; an error is thrown when those arguments are not passed in when the
method is called. So what do we do when we need to tell a method that we might
not have the information it expects?

When signing up on a social media website, you may notice there are options to
add personal information like a profile picture. However, when one isn't provided,
it defaults to a generic avatar image, like a silhouette of a person:

<img src="https://i.stack.imgur.com/l60Hf.png" alt="Default Facebook Avatar" width="200"/>

This can be done by using optional arguments with _default_ values. We could assume
that there's a method called `display_user_image(image_url)` that defaults to this
generic image UNLESS it's given a URL to a real image URL – your picture!

<img src="https://short-biography.com/wp-content/uploads/mark-zuckerberg/Mark-Zuckerberg.jpg" alt="Mark Zuckerberg, the found of Facebook" width="200"/>

With optional arguments, we're given the flexibility of omitting, or leaving out,
certain data. We're going to introduce how to create methods that take in optional
arguments and cover why they're important to programming.

## Define a Method With Optional Arguments

Default arguments are easy to add! You simply assign their corresponding parameters
a value with = in the parameter list in the method signature. There's no limit to
the number of arguments that you can make default.

```ruby
def greeting(name="Ruby programmer", language="Ruby")
  puts "Hello, #{name}. We heard you are a great #{language} programmer."
end
```

Let's take a look at the different ways we can call this method:

```ruby
greeting
# > Hello, Ruby programmer. We heard you are a great Ruby programmer.

greeting("Maria")
# > Hello, Maria. We heard you are a great Ruby programmer.

greeting("Steven", "Elixir")
# > Hello, Steven. We heard you are a great Elixir programmer.
```

Now, no matter whether an argument is passed in or not, text is output and no
errors are thrown.

## Define a Method With Optional and Required Arguments

It is possible to define a method that takes in both required and default
arguments. To do so, we  place the default argument at the **end** of the
argument list in the method definition. However, required arguments must
still be passed in:

```ruby
def greeting(name, language="Ruby")
  puts "Hello, #{name}. We heard you are a great #{language} programmer."
end

greeting # The method is called without arguments
```

If the expected arguments are not pass in, we will see an `ArgumentError`:

```bash
ArgumentError: wrong number of arguments (given 0, expected 1..2)
```

Now, let's call our `#greeting` method with a `name` given, with and
without an explicit `language` argument:

```ruby
greeting("Maria", "Ember.js")
# > Hello, Maria. We heard you are a great Ember.js programmer. 

greeting("Dan")
# > Hello, Dan. We heard you are a great Ruby programmer.
```

It works! 

## Conclusion

Method arguments, both required and optional, make methods abstract so that
we can cover a wide variety of usages while keeping our code DRY.
