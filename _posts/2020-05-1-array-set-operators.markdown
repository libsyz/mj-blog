---
layout: post
title:  "Array Set Operators"
date:   2020-04-27 23:48:01 +0800
categories: til
---

Ruby comes equipped with a bunch of amazing operators for Arrays.

Let's say I am working on lists of animals.

```ruby
animals_list = %w(duck tiger snake)
other_animals_list = %w(wolf duck tiger)
```

I might want to merge both lists, without duplicates.

```ruby
master_list = animals_list.concat(other_animals_list).uniq

#=> ["duck", "tiger", "snake", "wolf"]
```

Semantically, it feels too heavy to do two method calls for something so intuitive as a list without duplicates. Gladly, Ruby gives us the union operator

```ruby
master_list = animals_list | other_animals_list

#=> ["duck", "tiger", "snake", "wolf"]
```

How neat is that?

I might also want to extract which animals are common to both lists. Let's say I do something like

```ruby
all_animals = animals_list.concat(other_animals_list)
common_to_both = all_animals.keep_if { |animal| all_animals.count(animal) > 1 }.uniq

#=> ["duck", "tiger"]

common_to_both = all_animals.select {|animal| all_animals.count(animal) > 1 }

#=> ["duck", "tiger"]
```

Again, both approaches are heavy-handed and require two variable declarations. Again, Ruby has us covered with the intersection operator

```ruby
common_to_both = animals_list & other_animals_list

#=> ["duck", "tiger"]
```

We also can use the subtraction operator to compare arrays and see elements that are not shared

```ruby
uniq_to_animals_list = animals_list - other_animals_list
#=> ["wolf"]

uniq_to_other_animals_list = other_animals_list - animals_list
#=> ["snake"]
```

Another neat thing is that we can combine these operators with the equals operator. Let's say I want to update a list with elements of other lists, but I don't want to keep any duplicates.

```ruby
dirty_animal_lists = [["dolphin", "duck", "duck", "duck"],
											["lemur", "snake", "snake", "snake"]]

dirty_animal_lists.each { |list| animals_list |= list }

animals_list

#=> ["duck", "tiger", "snake", "dolphin", "lemur"]
```

The only downside to this approach is that animals_list gets reassigned every single iteration and it might be inefficient if you are working with huge things. For such cases, take a look at the Set documentation.
