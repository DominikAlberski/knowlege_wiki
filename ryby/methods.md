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
