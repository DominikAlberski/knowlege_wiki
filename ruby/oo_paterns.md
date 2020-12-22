### Decorator pattern
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
### Factory pattern
Factory is an object responsible for creating other objects based on given
requirements.
[refactoring guru](https://refactoring.guru/design-patterns/factory-method/ruby/example)

### Observer pattern
Observer is an object that "observs" behavior change or state change on other objects in my understanding it's similar to callbacks, but it's job is rather to inform about change and not to exactly act on it which should be done by other object.
observer pattern example [refactoring guru](https://refactoring.guru/design-patterns/observer/ruby/example)
[article on medium](https://medium.com/@mitchocail/observer-pattern-in-ruby-e80ac3c1dac7)

### Singelton pattern
In ruby it's implemented by including Singleton module into class.
This pattern is meant to ensure that only one instance of class will be present
By including Singleton module method new is set to private and we gain accessbrew to instance method instead

### State pattern
It's an representation of state machine. Every single state is represented by single class with logic discrabing transition to next state within given context.

### Builder pattern
This pattern is to useed in creation of complex objects. Exp. class containing amother class containing another class. As an reference look at [refactoring guru]

### Chain of responsibility
When object doesn't know how to respond to given method it should know who to ask for it. This pattern is implemented around method missing in ruby but from my understanding delegation should by fine for small amount of methods.

### Command
Allow for generic object to have different commends. Generic class can by instantiate with actions (aka other classes responsible for business logic), this classes are passed to object in arguments they have unified interface and can be executed exp:
```ruby
class Button
  def initialize(options)
    @label= options[:label]
    @action = options[:action].new
  end

  def click
    @action.execute
  end
end

class ExpAction
  def execute
    'do some stuff'
  end
end

class ExpAction2
  def execute
    'do some other stuff'
  end
end

Button.new(labe: "button_1", ExpAction).execute
=> 'do some stuff'

Button.new(labe: "button_1", ExpAction2).execute
=> 'do some other stuff'

```
### Mediator
It's an object that encapsulates logic responsible for other objects interactions

### Proxy
Proxy is similar to decorator in that way that its build with other object in mind but unlike decorator it's purpose is not to add functionality on top of existing one but rather restrict functionality of given object or provide some sort of restricted access to it.
