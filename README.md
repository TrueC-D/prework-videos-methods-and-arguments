# Methods and Arguments

## Learning Goals

+ Identify implicit return values in Ruby syntax
+ Describe the Functionality of Arguments
+ Use a method to execute pre-defined code
+ Define a method that takes in and uses an argument
+ Define a method that takes in and uses multiple  arguments
+ Define a method with an optional argument
+ Explain the importance of a return value of a method
+ Explain the importance of scope in programming
+ Identify the scope of a given variable
 
## Outline

+ Describe that we'll look at ways to organize our code. We could, if we wanted to, write our whole program just in order and have it run like a script, but we probably don't want to do that.
  + Difficult to read, difficult to maintain
  + We can instead, write re-usable chunks of code. 
+ Define a method
  + Like a little machine - takes in something, and either does some unit of work, or returns to us something
  ```ruby
  def greet_user
    puts "Hello!"
  end
  ```
  + This code does something, it simply prints out the word "Hello!" to our user. At first glance, you might not think we need to wrap it in a method.
  + But imagine that we have this all over our code base, and we want to change "Hello!" to Hi! Suddenly - this gets pretty tricky. 
  + But because we're using the method, we can make the change in one place, and it will automatically happen. Change "Hello" to "Hi!" to demonstrate.
+ Add an argument, and show how to access it. say hi to name.  
+ So this is a basic example of how to use a method to do something. Let's look now at how to return something. 
```ruby
def double(number)
  return number * 2
end
```
So this method, takes in a number, and returns that number * 2. 

```
doubled = double(2)
```
+ Show that doubled returns `4`. 

This is using an "explicit" return - in Ruby, if I use the `return` keyword, the method will stop there and return whatever I said. 
```ruby
def return_three
  return 3
  2
end
```
+ That method will "short circuit" on the first line and return 3
+ If we don't tell our method what to return, it will just return whatever the last line evaluates to. 
+ Look at these examples - pause the video and see if you can predict what these methods will return.
```
def two
  2
end

def hi
  "Hello"
  "Hi"
end

def times_three(number)
  number * 3
  false
end 
```
+ Review Scope
  + Let's take a look at scope for a second. 
  + Finally - let's take a look at scope. This is important to look at. Remember that there are only so many words in the english language. This means that we have a limited number of variable names to use. 
  + As our program grows, we want to re-use words in different contexts. So `number` in one place might be different than `number` someplace else. If I have these two methods:

```
def double(number)
  number * 2
end

def triple(number)
  number * 3
end
```

The numbers in each of those methods are actually different - I can't change what they are. Or consider this example:

```
def say_name
  name = "Grace"
  puts name
end

name = "Claire"
say_name
```

What will that print?  

This actually prints "Grace" - because remember, inside of that method call, they don't know about the name we defined outside the method
