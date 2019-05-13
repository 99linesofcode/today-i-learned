## GRASP - General Responsiblity Assignment Software Patterns/Principles

Guidelines for assigning responsibility to classes and objects in object oriented design.

## Table of Contents

- [The Controller](#the-controller)
- [The Creator and The Information Expert](#the-creator-and-the-information-expert)
- [Indirection](#indirection)
- [High Cohesion](#high-cohesion)
- [Low Coupling](#low-coupling)
- [Polymorphism](#polymorphism)
- [Protected Variations](#protected-variations)
- [Pure Fabrication](#pure-fabrication)

# The Controller

This type of object stands between the UI and coordinates system operations. In most situations, the controller represents the device that the software runs in. It is the object that connects to most other objects in your sequence diagram.

# The Creator and The Information Expert

When defining or or creating an object that should create another object:

Object A should create Object B if:

- Object A contains Object B
- Object A saves Object B to a file or a database
- Object A uses Object B
- Object A has all the data needed to instantiate Object B

In most situations more than one of these 4 rules is going to be true.

The `Creator` object should should instantiate the containing object and accept parameters instead of forcing the user to instantiate the classes themselves.

```php
class Bike {
  public function __constructor(int $wheelWidth, int $frameLength) {
    $this->wheel = new Wheel($wheelWidth);
    $this->frame = new Frame($frameLength);
  }
}
```

If Object A is going to Instantiate Object B, it must have all the info needed to create it. In other words, Object A must be an expert on how to create Object B.

# Indirection

..

# High Cohesion

A measure of how focused the responsibilities of an object are. A class should be very easy to comprehend, easy to maintain and easy to reuse.

Classes should handle very few responsibilities for one part of the system. Instead, you want to have many classes responsible for little parts of the system. This should result in classes with very few methods and they should work with others to fulfill a complicated need.

When in doubt, delegate!

# Low Coupling

A class with high coupling relies on many other classes. Such a class is:

1. Not reusable
2. Is hard to understand in isolation
3. Easily broken if other classes change
4. Harder to test

Let me show you an example:

```php
declare(strict_types=1);

class ListAnimals {
  private Monkey $monkey;
  private Lion $lion;

  public function listAnimals(Monkey $monkey, Lion $lion) {
    $this->monkey = $monkey;
    $this->lion = $lion;
  }

  public function display_animals(): string {
    echo $this->monkey->to_string() . "\r\n";
    echo $this->lion->to_string() . "\r\n";
  }
}

$monkey = new Monkey("Joe");
$lion = new Lion("Jax");
$listOfAnimals = new ListAnimals($monkey, $lion);

$listOfAnimals->display_animals();
```

What happens when you have to display new Animals in the future? In order for this code to support new functionality, it has to be modified in several places (the property list, constructor and the display_animals() method). This is bad.

Instead, what we want to do is make the ListAnimals class loosely coupled to the Animals it will have to display which we can achieve by employing polymorphism.

```php
declare(strict_types=1);

class Animal {
  private $name;

  public function __constructor(string $name) {
    $this->name = $name;
  }

  public function to_string(): string {
    echo "An Animal named " + $name;
  }
}

class Monkey extends Animal {
  private $name;

  public function __constructor(string $name) {
    parent::__construct();
    $this->name = $name;
  }

  public function to_string(): string {
    echo "A Monkey named " + $name;
  }
}

class ListAnimals {
  private $listOfAnimals = [];

  public function add_animal_to_list(Animal $newAnimal): void {
    array_push($this->listOfAnimals, $newAnimal);
  }

  public function display_animals(): string {
    array_walk($this->listOfAnimals, function($animal, $key) {
      echo $animal->to_string();
    });
  }
}

$monkey = new Monkey("Louie");
$listAnimals = new ListAnimals();
$listAnimals->add_animal_to_list($monkey);
$listAnimals->display_animals();
```

By structuring our code this way, we avoid having to make modifications to the `ListAnimals` class and guarantee that any Object passed into the `add_animals_to_list` method is of the type or a subtype of `Animal`.avoid being tied to specific classes and opened our class up for extension.

Below is a list of the different types of coupling that might exist between two classes (from loose to highly coupled):

| Levels of coupling | Description                                                                         |
| ------------------ | ----------------------------------------------------------------------------------- |
| Dependence         | The class depends on another class but it isn't a member of that class ie. `Uses A` |
| Association        | The class contains a reference to another class ie. `Has A`                         |
| Composition        | The class holds an instance of another class ie. `Owns A / Part of A`               |
| Inheritance        | The class implements or extends another class `Is A`                                |

So, in order to achieve low coupling you need to:

1. Design classes that are independent so that changes in other classes have no effect;
2. Avoid creating sub classes and if you do sub class interfaces or abstract classes;
3. Add flexibility and encapsulation to classes to avoid major problems from high coupling.

# Polymorphism

..

# Protected Variations

..

# Pure Fabrication

..
