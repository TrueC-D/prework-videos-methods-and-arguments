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

## Lesson
<iframe width="100%" height="720" src="https://www.youtube.com/embed/8_E9e1RUGU0?rel=0&showinfo=0" frameborder="0" allowfullscreen></iframe>

+ Hey folks, it's Ian from Flatiron School. In this video, we're going to look at using methods and arguments in Ruby.
+ Our learning goals for this video:
  + Identify implicit return values in Ruby syntax
  + Describe the Functionality of Arguments
  + Use a method to execute pre-defined code
  + Define a method that takes in and uses an argument
  + Define a method that takes in and uses multiple  arguments
  + Define a method with an optional argument
  + Explain the importance of a return value of a method
  + Explain the importance of scope in programming
  + Identify the scope of a given variable

### Using Methods to do work
+ So, let's get started. One thing that we want to do as developers is to keep our code organized. We could, if we wanted to, write our whole program just in order and have it run like a script
+ There are some down sides to doing that though. For one, it's difficult to maintain that code. If you have more than one person editing a file, changes you make in one part of the file are going to affect things in another part, so it's going to be really difficult to keep track of.
+ It's also really hard to read - because you have to read the whole thing in order.
+ Instead, we need a way to keep things organized, small, and clean.
+ One way to do that is by defining methods. A method is like a little machine that does something or returns to us something.
+ We define a method by using the `def` keyword and then writing what we want our method to be named. By convention in ruby, we use what's called snake_case - all lower case letters with underscores instead of spaces
+ Let's demonstrate what I mean by a method that does something. I'm going to write a method that prints out a greeting.
  ```ruby
  def greet_user
    puts "Hello!"
  end
  ```
  + This method, `greet_user`, is code that does something, it simply prints out the word "Hello!" to our user. At first glance, you might not think we need to wrap it in a method.
  + But imagine that we have this all over our code base, and we want to change "Hello!" to Hi! Suddenly - this gets pretty tricky.
  + But because we're using the method, we can make the change in one place, and it will automatically happen. I simply edit the method once:
  ```ruby
  def greet_user
    puts "Hi!"
  end
  ```
+ So already, this makes our code easier to maintain. We can make this even more dynamic with an argument. Let's say that we want to be able to include someone's name in the message.
+ I can do this using arguments. Arguments let us pass values into a method to be used dynamically.
```ruby
def greet_user(name)
  puts "Hi, #{name}!"
end
```
+ I can call this method and pass in any value that I want. This let's me flexibly greet any person that I want to.
+ There's no limit to how many arguments a method can take in (though generally best practice is to limit it to four parameters or less - if you have a method that needs more than four arguments, there's probably another way to do the thing you're trying to do.)
+ You just give them different names.
```ruby
def greet_user(greeting, name)
  puts "#{greeting}, #{name}!"
end

greet_user("Ahoy", "Grace")
greet_user("Hello", "Jennifer")
```
+ You can also give a method a default value for an argument. This lets you call it even more flexibly.
```ruby
def greet_user(name="friend")
  puts "Hello, #{name}!"
end

greet_user("Grace")
greet_user
```
+ So this is a basic example of how to use a method to do something, and all about arguments.
### Using Return Values
+ Let's look now at how we can use return values of methods. So we mentioned our methods are like little machines.
+ Some machines in the real world do something for us - think of a door bell.
+ You press the button - it rings a bell (or makes a bell sound)
+ Other machines take in inputs and return to us output.
+ Think of a toaster - the input is a slice of bread, the output is toast.
+ We can use methods to make machines like this as well - they can take in inputs, and give us back outputs.
+ Let's write a method to double a number
```ruby
def double(number)
  return number * 2
end
```
So this method, takes in a number, and returns that number * 2.

```
doubled = double(2)
```
+ The variable doubled is equal to the return value of the method.
+ This is using an "explicit" return. Ruby also had what's called implicit return - this just means that, unless I say otherwise, the return value will be the last line of the method.
```ruby
def double(number)
   number * 2
end
```
+ This code will function exactly the same as it did before.
+ One thing about an explicit return - as soon as the Ruby method sees the return keyword, it's going to stop and not continue. Look at this method:
```ruby
def return_three
  return 3
  2
end
```
+ That method will "short circuit" on the first line and return 3. It won't continue on to the second line of the method. This is mainly useful if you have a condition or something.
```ruby
def do_something_on_saturdays(day)
  if day != "Saturday"
    return
  end
  # Do a bunch of stuff here
end
```
+ So we've talked about return values - let me write out a couple of examples here. Go ahead and pause the video and see if you can predict what these will return.
```ruby
def example_one
  2
end

def example_two
  "Hello"
  "Hi"
end

def example_three
  return "Hello"
  "Hi"
end

def example_four(number)
  number * 3
  false
end
```
+ So, our first example, has just one line, 2. The last line evaluated is `2` - so `2` is our return value.
+ Our Second Example evaluates two lines - the last line evaluated is "Hi", so "Hi" is the return value
+ In our third example, we return "Hello" explicitly on the first line, so the return value is "Hello"
+ In our fourth example, we calculate a number, but the last line evaluated is just false. So this method returns false.
+ One last note on return values is on the `puts` method. The `puts` method prints something, but actually returns nil. So our greet_user method from before, will return nil.
+ So a lot of times, you either want your method to do something like print, or you want it to return something, One way around this is to use two methods.
```ruby
def greeting(name)
  "Hello, #{name}!"
end

def print_greeting(name)
  puts greeting(name)
end
```
### Scope
+ Finally - let's take a look at scope. This is important to look at. Remember that there are only so many words in the English language. This means that we have a limited number of variable names to use.
+ As our program grows, we want to re-use words in different contexts. Take a look at the following example:
```ruby
name = "Bob"
def hello
  puts "Hello, #{name}"
end

hello
```
+ What will happen when I run this code? This actually throws an error - `undefined local variable or method name`
+ Why might that be? Because each time I define a method, I create what's called a scope gate. It's like it's own little universe with it's own set of local variables.
+ Variables outside are in a different universe. Variables created inside are also in a different universe.
```ruby

def dog
  dog = "Fido"
end

dog #=> undefined
```
+ So remember that local variables won't cross in or out of method definitions. This might seem weird, but it's actually really important. We need to be able to re-use those method names for different things!

### Conclusion
+ So that's it for this video. Just to recap, today we learned:
  + That Ruby methods implicitly return the last line they evaluate
  + That we can use arguments to access things inside of methods
  + That methods will execute a pre-existing piece of code
  + That methods can have 0, 1, or many arguments
  + How to use a method with an optional argument
  + Some times when we would use a method's return value
  + Why scope is important in programming
  + And how to identify the scope of a given variable in a method
+ Thanks for watching, and happy coding!
