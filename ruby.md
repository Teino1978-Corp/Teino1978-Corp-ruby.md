#Ruby

##Table of Contents

1. [Introduction](#introduction)
2. [Setup](#setup)
3. [Interaction](#interaction)
4. [Strings](#strings)
5. [Numbers](#numbers)
6. [Collections](#collections)
7. [Symbols](#symbols)

<a name="introduction">
##Introduction
</a>

###What is it?

Ruby is a dynamic server-side programming language created by Yukihiro "Matz" Matsumoto in Japan in the mid-1990s.  It was influenced heavily by the Perl, Smalltalk, and Lisp programming languages. The philosophy that underpins Ruby was articulated best during a Google Tech Talk in 2008 when Matsumoto himself said, "I hope to see Ruby help every programmer in the world to be productive, and to enjoy programming, and to be happy."

###Resources

Here are a few great resources to play around with Ruby on your own:
+ [tryruby.org](http://tryruby.org/)
+ [Ruby in 20 Minutes](https://www.ruby-lang.org/en/documentation/quickstart/)
+ [13 Ways of Looking at a Ruby Symbol](http://www.randomhacks.net/2007/01/20/13-ways-of-looking-at-a-ruby-symbol)

<a name="setup">
##Setup
</a>

You can check to see if you have Ruby on your machine (Linux or Mac) by opening up a terminal and running `ruby -v`, which will display the currently installed version (or an error if it's not installed).  For more explicit setup instructions, go [here](https://github.com/Teino1978-Corp/Teino1978-Corp-ruby-on-rails.md).

<a name="interaction">
##Interaction
</a>

You can interact with the ruby language using `irb` or "Interactive Ruby Shell."  Below is a sample:

```
$ irb
irb(main):001:0> puts "Hello, World"
Hello, World
 => nil
irb(main):002:0> 1+2
 => 3
```

<a name="strings">
##Strings
</a>

There are a multitude of ways to define a string in Ruby. Here are a few ways:
```
string = "This is a string"
string = %Q{This is a string}
string = %{This is a string}
string = %/This is a string/
string = <<-BLOCK

This is a string
BLOCK
```

Another thing to note about strings in Ruby is that they support [variable interpolation](https://en.wikipedia.org/wiki/String_interpolation), as shown here:

```
var = 3.14159
"pi is approximately #{var}."
=> "pi is approximately 3.14159."
```

<a name="numbers">
##Numbers
</a>

With Ruby, you can interact with and manipulate numbers in much the same ways you can in most other languages.

###Basic Math

```
3 + 4   # Addition
=> 7

3 - 4   # Subtraction
=> -1

9 * 9   # Multiplication
=> 81

24 / 3  # Division
=> 8

15 % 4  # Modulo (Remainder)
=> 3

3 ** 3  # Powers
=> 27
```

###Number Types

Like other languages, Ruby identifies numbers as integers (Fixnum) and floats (Float):

```
666.class
=> Fixnum

3.14159.class
=> Float
```

<a name="collections">
##Collections
</a>

Ruby uses arrays and hashes (associative arrays) to make sense of collections of data.

###Arrays

Construct:
```
array = [1, 'hi', 3.14, 1, 2, [4, 5]]
```

or

```
array = %w(1 hi 3.14 1 2 [4, 5])
```

Access:
```
array[2]
=> 3.14

array.[](2)
=> 3.14

array.at(0)
=> 1

array.first
=> 1

array.last
=> [4, 5]

array.length
=> 6

array.include?('hi')
=> true
```

Manipulate:
```
grocery_list = ["milk", "eggs", "bread"]
=> ["milk", "eggs", "bread"]

# Add to end of the array
grocery_list << "carrots"
grocery_list.push("carrots")
grocery_list += ["ice cream", "pie"]

# Add to the beginning of the array
grocery_list.unshift("celery")

# Add at a specific location in the array
grocery_list.insert(2, "oatmeal")

# Remove the last item of the array
grocery_list.pop

# Remove the first item of the array
grocery_list.shift
```

###Hashes (Associative Arrays)

Construct:
```
# Below are identical
hash = Hash.new
hash = {}

# Below are similar, but NOT identical (try accessing each in irb to see the differences)
item = { :name => "Bread", :quantity => 1 }
item = { "name" => "Bread", "quantity" => 1 }
item = { name: "Bread", quantity: 1 }
```

Access:
```
pets = { :dog => 'woof', :cat => 'meow', :fox => 'https://www.youtube.com/watch?v=jofNR_WkoCE' }

puts pets[:dog]
woof
=> nil

pets.keys
=> {:dog, :cat}

pets.has_key?(:sloth)
=> false

pets.has_value?('meow')
=> true

puts "Hash: #{pets.inspect}"
Hash: { :dog => 'woof', :cat => 'meow' }
```

Loop:
```
pets.each do |key, value|
  puts "#{key} goes #{value}"
end
dog goes woof
cat goes meow
fox goes https://www.youtube.com/watch?v=jofNR_WkoCE
=> {:dog=>"woof", :cat=>"meow", :fox=>https://www.youtube.com/watch?v=jofNR_WkoCE}
```

Manipulate:
```
pets.delete(:fox)
=> "https://www.youtube.com/watch?v=jofNR_WkoCE"
```

<a name="symbols">
##Symbols
</a>


###What are they?
Symbols are a peculiarity. It looks like a variable name, only it's prefixed with a colon. In a nutshell, symbols in Ruby are Objects that represent names (and sometimes strings). They are powerful because they are efficient. Where two strings with the same content are actually two different objects in memory, for any given name there is only one Symbol object.

So, A Ruby symbol is a constant, unique name:

```
# String
"foo".object_id != "foo".object_id
=> true

# Symbol
:foo.object_id == :foo.object_id
=> true
```

This leads me to another important point -- symbols are immutable. A symbol's value will not change throughout the life of your program.

###When to use

Here is a clear and easy way to decide when to use symbols:

+ If the *contents* (the sequence of characters) of the object are important, use a **string**
+ If the *identity* of the object is important and needs to be the same througout a program, use a **symbol**