#### The `Factory` pattern
> Uses factory methods to deal with the problem of creating objects without having to specify the exact class of the object that will be created.

Having a dedicated factory object means multiple classes can use its behavior for other purposes. This generalisation encapsulates the creational behavior. By defining an abstract base class and forcing subclasses to implement an abstract method, other objects can confidently make calls to the abstract method, regardless of the subclass that is being passed in.

`Note: This is what we call: "Code to an interface, not an implementation"`

##### When would you use this pattern?
- When you don't know ahead of time what class object you need
- When all of the potential classes are in the same subclass hierarchy
- To centralize class selection code
- When you don't want the user to have to know every subclass
- To encapsulate object creation

```php
namespace ACME;

class Client
{
  public function someOperation() {
    $factory = new ACME\SpaceShipFactory();
    $factory->makeSpaceShip('RocketSpaceShip');
  }
}

class SpaceShipFactory
{
  public function makeSpaceShip(string $ship): SpaceShip {
    switch($ship) {
      case "BattleCruiser":
        return new ACME\BattleCruiser();
        break;
      case "HeavyDestroyer":
        return new ACME\HeavyDestroyer();
        break;
      default:
        return null;
    }
  }
}

class BattleCruiser extends SpaceShip {
  public function __construct() {
    $this->setName("BattleCruiser");
    $this->setDamage(40);
  }
}

abstract class SpaceShip
{
  private $name = '';
  private $amountOfDamage = null;

  // force the extending class to implement this method
  abstract function createShip(string $ship);

  public function getName(): string { return $this->name; }
  public function setName(string $name): string { $this->name = $name; }

  public function getDamage(): int { return $this->amountOfDamage; }
  public function setDamage(int $dmg) { $this->amountOfDamage = $dmg; }
}
```
