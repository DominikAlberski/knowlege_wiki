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
# Factory pattern
Factory is an object responsible for creating other objects based on given
requirements.
[refactoring guru](https://refactoring.guru/design-patterns/factory-method/ruby/example)

# Observer pattern
Observer is an object that "observs" behavior change or state change on other objects in my understanding it's similar to callbacks, but it's job is rather to inform about change and not to exactly act on it which should be done by other object.
observer pattern example [refactoring guru](https://refactoring.guru/design-patterns/observer/ruby/example)
[article on medium](https://medium.com/@mitchocail/observer-pattern-in-ruby-e80ac3c1dac7)

# Singelton pattern
In ruby it's implemented by including Singleton module into class.
This pattern is meant to ensure that only one instance of class will be present
By including Singleton module method new is set to private and we gain accessbrew to instance method instead
