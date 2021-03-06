`method`
Use on instance of a class with method name as parameter.
Combine with `owner` it allows to determine on which class the method was defined.

```ruby
  example.method('greet').owner
  #<Class:SomeExample::Base>
```

---

`source_location`
Provides exact information of file name and line number of method definition.
Very handy to finding about some unknown methods from modules etc.

---

`filter_map`
Combines filter and map exmp:
```ruby
  data.filter_map { |d| d if :condition }
  # => [...]
```

---

`detect`
returns first value from enumerable that for given block returns true
```ruby
  data.detect { |d| d == :something }
  # => :something
```

---

`each_slice`
enumarator method for procesing in batches of given size
```ruby
  array.each_slice(5) { |batch| "batch.each(&.smg)" }
  # => enumerator
```

---

`tap`
it's used to "tap into" method chain and do something with intermittent values
```ruby
  array
    .map(&:do_something)
    .tap { puts "arra_item_after_something: #{_1.inspect}"}
    .map(&:do_smg_else)
```

in example it's used for debugging purposes

---

`grep`
Enumerable method that can replace such call:
`[].select { |x| \pattern\ === x }`

example:
```ruby
%[dolary centy].grep(/do/) # => ["dolary"]
%[dolary centy].grep(/do/) { |x| x + " $" } #=> ["dolary $"]
```

Argument for grep don't have to be regexep,
it can be any other object that implements `===`

---

throw catch behavior
when throw is inside catch block it will omit any rescue in that block
```ruby
catch(:halt) do
  begin
    throw :halt
  rescue Exception => exception # this will not be executed
    puts "rescue: #{exception.inspect}"
    raise
  ensure
    puts "ensure"
  end
end
```
