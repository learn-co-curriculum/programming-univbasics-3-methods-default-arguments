# Title

## Learning Goals

- Recognize the benefits of optional arguments
- Define a method with optional arguments
- Define a method with optional and required arguments

## Introduction

If we revisit the coffee shop scenario, typically a name may be given when you
place your order so that your name can be called when the order is ready. What
happens when they don't ask for a name? Usually, they _default_ to calling out
the order that was placed. This may not be as personalized to you, but it's
better than not knowing when your order is ready!

In Ruby, we now see that when a method accepts arguments, those arguments become
required; an error is thrown when those arguments are not passed in on
invocation of the method. So what do we do when we have optional information?

When signing up on a website, you may notice that if there are personalization
options like a profile picture. However, when one isn't provided, it defaults to
a generic avatar image, like a silhouette of a person.

!["Default Facebook Avatar"](https://i.stack.imgur.com/l60Hf.png)

This can be done by using optional arguments with _default_ values. We're going
to introduce how to create methods that take in optional arguments and cover why
they're important to programming.

## Recognize the Benefits of Optional Arguments

We should constantly strive for our code to be dynamic and flexible. As
programmers, we might be considered lazy, but why do more work than is
necessary? We want the code we write to be re-usable, which is why we have
principles such as DRY.

If we define a method, `#greeting`, without arguments, it'll be very difficult
to reuse this code in any other manner. Since that's way too much work for us,
we'll define our method to take in an _argument_ of someone's name:

```ruby
def greeting(name)
  puts "Hello, #{name}"
end
```

But what if we don't know the name of the person we are trying to greet? We can
make this method even more flexible by making the `name` argument optional. We
do this by using optional, or default, arguments.

## Define a Method With Optional Arguments

Default arguments are easy to add, you simply assign them a default value with
`=` ("equals") in the argument list. There's no limit to the number of arguments
that you can make default.

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
argument list in the method definition.

Take a look:

```ruby
def greeting(name, language="Ruby")
  puts "Hello, #{name}. We heard you are a great #{language} programmer."
end
```

Let's call our `#greeting` method with and without an explicit `language`
argument:

```ruby
greeting("Maria", "Ember.js")
# > Hello, Maria. We heard you are a great Ember.js programmer. 

greeting("Dan")
# > Hello, Dan. We heard you are a great Ruby programmer.
```

It works! Why must we place the default argument at the end of the argument
list?

Let's take a look at what would happen if we didn't:

```ruby
def greeting(language="Ruby", name)
  puts "Hello, #{name}. We heard you are a great #{language} programmer."
end
```

Now, what happens when we try to call our method without an explicit `language`
argument?

```ruby
greeting("Maria")
```
You might expect it to break. Or you might expect it to think that the
`language` variable is being set equal to `"Maria"` in this method call. 

Neither of those things will happen. The method will work as we intended because
Ruby is smart and has a few tricks up its sleeve to help determine what method
arguments are being used where in a method's body. 

However, defining the default argument first is confusing. We can understand
this from our very reasonable expectations that the above method invocation
would break. For this reason, it is conventional to place any default arguments
at the end of an argument list when defining a method that takes in both
required and default arguments. 


## Conclusion

Method arguments, both required and optional, make methods powerfully abstract
and dynamic machines that are easy to build yet very flexible and adaptable to
different situations and requirements. Get used to defining methods with
required and default arguments and calling them correctly.

## Resources
