# Named groups

allows to return matched results as named basic example:

```ruby
  string_to_check = "NR: 43-555-456 42-555-123"
  regex = /NR:\s(?<first_number>\d{2}-\d{3}-\d{3})\s(?<second_number>\d{2}-\d{3}-\d{3})$/
  match_obj = string_to_check.match(regex)
  match_obj["first_number"]
  # => "43-555-456"
  match_obj["second_number"]
  # => "42-555-123"
```
[article](https://makandracards.com/makandra/70443-ruby-using-named-groups-in-regex)
