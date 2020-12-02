# Decorator pattern
Docorateor is an object that takes as an argument other object and adds new functionalities to it.
As an simple example User has a name and surname as separeted fileds and user decorator has fullname method.
```ruby
class User
  attr_accessor :name, :surname

  def initilize name surname
    self.name = name
    self.surname = surname
  end
end

class UserDecorator
  delegate :name, :surname, to: :user

  attr_accesspr :user

  def initilize user
    self.user = user
  end

  def fullname
    format('%<name>s %<surname>s', name: name, surname: surname)
  end
end
```
