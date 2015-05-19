angular-typescript-cheatsheet

# module

```js
module services {

  //...
  class MyService {
    //...
  }
  
  angular.module('services', ['dependency']).service('MyService', MyService);  
}
```

# dependency injection

inside a class:

```js
class MainCtrl {

  static $inject = ['$scope', 'MyAnimalFactory'];
  
  constructor($scope: ng.IScope, factory: MyAnimalFactory) {
    //...
  }
}
```

# class

```js
class MainCtrl {
  name: string = 'default';
  list: Array<Animal> = [];
  
  constructor() {
    this.name = 'dog';
  }
}
```

# service

```js
module services {

  //more classes: ...

  class AnimalFactory {
  
    //... more classes
    
    getInstance(type: string, name: string) {
      var clazz = null;
      if(type === 'mammal') {
        clazz = Mammal;
      } else if(type === 'reptile') {
        clazz = Reptile;
      } else {
        clazz = Animal;
      }
      return new clazz(name);
    }    
  }

  angular.module('animals',[]).service('MyAnimalFactory', AnimalFactory);
}

//Usage:
//...
static $inject = ['$scope', 'MyAnimalFactory'];
//...
```

# types

