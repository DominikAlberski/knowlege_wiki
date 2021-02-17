`method`
Use on instance of a class with method name as parameter.
Combine with `owner` it allows to determine on which class the method was defined.

```ruby
  example.method('greet').owner
  #<Class:SomeExample::Base>
```

`source_location`
Provides exact information of file name and line number of method definition.
Very handy to finding about some unknown methods from modules etc.

`filter_map`
Combines filter and map exmp:
```ruby
  data.filter_map { |d| d if :condition }
  # => [...]
```

`detect`
returns first value from enumerable that for given block returns true
```ruby
  data.detect { |d| d == :something }
  # => :something
```
`each_slice`
enumarator method for procesing in batches of given size
```ruby
  array.each_slice(5) { |batch| "batch.each(&.smg)" }
  # => enumerator
```

`tap`
it's used to "tap into" method shain and do soething with intermintet values
```ruby
  array.map(&:do_something).tap {puts "arra_item_after_something: #{_1.inspect}""}.map(&:do_smg_else)
```
in example it's used for debugging pouposes
