---
layout: post
title: "Dinner Club"
date: 2015-06-05
categories: code technical omahacodeschool
---

The assignment was to write a program that collects member names, restaurant names, and meal totals to track outings for a dinner club. The program should also include the ability to track attendance even if one member chose to pay for the entire meal.

The CheckSplitter class exists to calculate the meal total, including the tip, and then split that total evenly among the members who attended the outing. The DinnerClub class keeps track of member names and the outing history, as well as creating a case to allow a single member to pay for the entire meal if desired.  

## CheckSplitter
When CheckSplitter is initialized it requires three arguments, all of which are integer values: total\_cost\_of\_meal, tip\_percentage and  num\_people. Three corresponding attributes are created as well.

```ruby

  def initialize(total_cost_of_meal, tip_percentage, num_people)
    @total_cost_of_meal = total_cost_of_meal
    @tip_percentage = tip_percentage
    @num_people = num_people
  end
  
```

The even\_split method takes the total cost of the meal\_plus\_tip and @num\_people and calculates the amount each dinner club member owes for the meal.

```ruby

  def even_split
    meal_plus_tip / @num_people
  end
  
```

The meal\_plus\_tip method calculates the tip amount and adds it to the @total\_cost\_of\_meal in one step.

```ruby

  def meal_plus_tip
    @total_cost_of_meal * (tip_as_decimal + 1)
  end
  
```

The tip\_as\_decimal method compensates for the possibility of the user entering the tip in decimal form. If the tip is entered as an integer percentage amount, it is converted to decimal form.

```ruby

  def tip_as_decimal
    if @tip_percentage >= 1
      tip_as_decimal = @tip_percentage / 100.0
    else
      tip_as_decimal = @tip_percentage
    end
  end
  
```

## DinnerClub
This class takes one argument, member\_names, as an array when it is initialized. It has two attributes, @members and @history, which are each initialized as an empty hash. 

```ruby

  def initialize(member_names)
    @members = {}
    @history = {}
    
```

This iterates over the member\_names array and adds each name as a key to the empty @members hash with a default value of zero.

```ruby

    member_names.each do |name|
      @members[name] = 0
    end      
  end
  
```

The go\_out method is defined with five arguments: one\_guest\_pays, paying\_guest, meal\_cost, tip\_percent, and attendees. When the go\_out method is called a new instance of the CheckSplitter class, called cs, is then instantiated.

```ruby

  def go_out(one_guest_pays, paying_guest, meal_cost, tip_percent, attendees)
    cs = CheckSplitter.new(meal_cost, tip_percent, attendees.length)
    
    amount_per_person = cs.even_split
    treat = cs.meal_plus_tip
    
```

The one\_guest\_pays case requires the user to confirm whether or not the meal will be split evenly. If false is returned, it requires the user to provide the name of the paying member, and meal\_plus\_tip is called on cs to calculate the appropriate member total. If true is returned, even\_split is called on cs to split the check and update the total of each attendee.

```ruby

  case one_guest_pays
  when false
    treat = cs.meal_plus_tip
    @members[paying_guest] += treat
  when true
    amount_per_person = cs.even_split
    attendees.each do |n|
      @members[n] += amount_per_person
    end
  end
  
```

The history method adds to the empty hash @ history with key: restaurant and value: the array of attendees. This allows the user to view a hash of the restaurants the dinner club has visited along with an array value showing the corresponding attendees at each restaurant outing.

```ruby

  def history(restaurant, attendees)
    @history[restaurant] = attendees
  end
  
```