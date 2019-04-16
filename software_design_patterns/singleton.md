#### The `Singleton` pattern
> Ensures that a class has only one instance and provide a global point of access to it.

```php
class MySingleton
{
  private static $instance = null;

  private __construct() {}

  public static function getInstance(): MySingleton {
    if( ! isset(self::instance)) {
      self::instance = new MySingleton();
    }

    return self::instance;
  }
}
```

As the getInstance() method is static it is possible to gain access to the MySingleton instance from anywhere. An added benefit of using the singleton pattern is that the objection is not created until it is truly needed ([lazy initialization](https://en.wikipedia.org/wiki/Lazy_initialization)).

`Note: be careful with this design pattern in multi-threaded environments`

##### When would you use this pattern?
- [Singleton, I love you but you're bringing me
  down](http://geekswithblogs.net/AngelEyes/archive/2013/09/08/singleton-i-love-you-but-youre-bringing-me-down-re-uploaded.aspx)


