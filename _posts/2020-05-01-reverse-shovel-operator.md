---
layout: post
title:  "The >> Operator"
date:   2020-04-27 23:48:01 +0800
categories: til
---

Ruby gives us a neat pice of syntax to compose procs in a readable way.

Let's say I want the addition of two numbers

```ruby
add = proc { |first, second| first + second }
add.call(1,2)
# => 3
```

Let's say I would also like my program to square numbers

```ruby
square = proc { |number| number ** 2 }
square.call(2)
# => 4
```

Now, I would like the program to perform one action after the other. First add two numbers, and then square them

```ruby
add_then_square = square.call(add.call(1,2))
# => 9
```

I tried composing two simple functions and I don't like where this is going.  Now I need to read the line from left to right. This is when the `>>` operator comes in to make our day.

```ruby
add_then_square = add >> square
add_then_square.call(1,2)
# => 9
```

You can also reverse the order of operations by using <<

```ruby
greet = proc { |name| "Hello, #{name}!" }
sanitize_name = proc {|name| name.capitalize }

say_hello = greet << sanitize_name
say_hello.call("BENDER")

# =>  "Hello, Bender!"
```

And we do not even have to assign multiple procs to a variable in order to  call them.

```ruby
total = 0
appetizer = proc { total += 10 }
salad = proc { total += 15 }
dessert = proc { total += 6 }

(appetizer >> salad >> dessert).call

# => 31
```

All this makes composing and pipelining behavior really easy. Procs are, however, one of the very few things in Ruby that are not objects. We need to add a bit of indirection to our methods if we want to make them compatible with `>>`.

```ruby
def sanitize_name
  proc { |n| n.capitalize }
end

def verify_robot
  robot_names = %w(Bender Marvin Kitt)
  proc {|n| n if robot_names.include?(n) }
end

def greet
  proc {|n| "Hello ,#{n}!" }
end

join_robot_army = sanitize_name >> verify_robot >> greet
join_robot_army.call("BENDER")

# =>  "Hello, Bender!"
```

Ruby is famous for being an OOP-first language, but it has great support for function composition and creating pipes. The `>>` operator is part of it, but there's also bautiful language features like #then and `===`.
