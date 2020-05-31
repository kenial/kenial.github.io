---
title: "C# 코드로 살펴보는 공변성 / 반공변성의 예"
date: "2020-05-31T16:57:00+09"
template: "post"
draft: false
slug: "/posts/csharp-example-of-covariance-contravariance/"
category: "Tech"
tags:
  - "Tech"
  - "C#"
  - "공변성"
  - "Covariance"
  - "반공변성"
  - "Contravariance"
description: "공변성(Covariance)과 반공변성(Contravariance)은 클래스/타입의 변환이 일어날 때 변환의 방향이 상위 → 하위 (ie. 부모 → 자식) 방향으로 일어나는지 혹은 그 반대 방향으로 일어나는지를 말한다."
---

공변성(Covariance)과 반공변성(Contravariance)은 클래스/타입의 변환이 일어날 때 변환의 방향이 상위 → 하위 (ie. 부모 → 자식) 방향으로 일어나는지 혹은 그 반대 방향으로 일어나는지를 말한다. 객체지향 프로그래밍을 배운 사람이라면, 공변성은 흔히 볼 수 있는 변환이다. 아래와 같이 동물(Animal) > 포유동물(Mammal) > 고양이(Cat)라는 상속 관계가 있다고 해 보자. 


    class Animal
    {
        public void DoAnimal() { }
    }
    
    class Mammal : Animal
    {
        public void DoMammal() { }
    }
    
    class Cat : Mammal
    {
        public void DoCat() { }
    }

위 클래스를 가지고 어떤 타입 변환이 가능할까? Mammal 타입 변수에 Cat 객체를 할당하는 경우를 생각해 볼 수 있다. Cat 객체는 Mammal 객체가 가진 동일한 메서드와 속성을 갖추고 있기 때문이다.


    Mammal mammal = new Cat();

위와 같이 서브타입 → 수퍼타입으로의 변환을 공변성(Covariance)이라고 한다. 이러한 내용은 객체지향 프로그래밍을 배운 사람이라면 누구나 익숙할 것이다. 하지만 Generic을 사용할 경우 타입 인자가 어디에 있느냐에 따라 변환의 방향이 수퍼타입 → 서브타입이 되는 경우가 있다. 다음 예를 살펴보자.


    class Reptile : Animal { }
    class Snake : Reptile { }
    
    ...
    
    var cat = new Cat();
    var snake = new Snake();  // a snake is a reptile
    
    IEnumerable<Animal> animals = new List<Mammal> { cat };
    animals.First().DoAnimal();
    
    IEnumerable<Mammal> mammals = new List<Animal> { snake };  // error!
    mammals.First().DoMammal(); 
    
    Action<Mammal> actionFromCat = (Action<Cat>)(c => c.DoCat());  // error!
    actionFromCat(cat);
    
    Action<Mammal> actionFromAnimal = (Action<Animal>)(a => a.DoAnimal());
    actionFromAnimal(snake);  // error!

4행 구문은 두 부분으로 나눠서 봐야 한다. 


1. `new List<Mammal> { cat }` 에서는 Cat 객체가 List<Mammal>의 객체 이니셜라이저에 전달되는데, Cat 타입 객체는 Mammal 타입의 모든 메서드와 속성을 구현하고 있으므로, List<Mammal>에서 인출되었을 때 Mammal 객체가 하는 일을 모두 할 수 있다. 그러므로 이 변환은 적법하다.
2. 이렇게 생성된 List<Mammal> 타입 객체가 IEnumerable<Animal> 타입 변수에 할당되는데, List<T> 타입은 IEnumerable<T> 인터페이스의 모든 메서드를 구현하고 있으며, Mammal 또한 Animal의 모든 메서드와 속성을 구현하고 있으므로, 3행에서의 변환은 안전(safe)하다.

7행 구문에서는 List<Animal> 타입 객체를 IEnumerable<Mammal> 타입 변수에 할당하려고 시도하는데, List<T> → IEnumerable<T> 변환은 가능하지만 Animal → Mammal로의 변환이 불가능하다. List<Animal> 컬렉션은 Cat 타입 객체 외에도 다른 동물, 예를 들면 Snake를 포함할 수 있으며, Snake는 Mammal 타입의 서브타입이 아니기 때문이다. Snake는 DoMammal을 할 수 없지만, 그와 별개로 8행 구문에는 문제가 없다.

10행 구문을 살펴보자. Action<Mammal> 타입은 Mammal 타입을 인자로 받는 메서드를 의미한다. 여기서 Action<Cat> 타입 → Action<Mammal> 타입으로의 변환을 시도하는데, 이 경우에는 변환이 실패한다. Action<Mammal> 타입은 Cat만이 할 수 있는 DoCat() 메서드를 호출하는 인자를 받는 함수를 처리할 수 없기 때문이다. 하지만 11행은 문제가 없다. actionFromCat은 Mammal을 인자로 받고, Cat은 Mammal이 할 수 있는 일을 모두 할 수 있기 때문이다.

13행 구문은 위 예와 반대 경우다. Action<Animal> 타입 → Action<Mammal> 타입으로의 변환은, Action<Mammal> 타입이 Animal 타입의 인자를 받는 함수를 처리할 수 있다. 하지만 14행 구문에서, actionFromAnimal은 Mammal 타입을 인자로 받기 때문에 Snake 타입 변수를 인자로 받을 수 없고, (Snake는 DoAnimal()을 호출할 수 있음에도 불구하고) 에러가 발생한다.

13행의 경우와 같이, Action<Animal> 타입 → Action<Mammal> 타입처럼 수퍼타입 → 서브타입의 변환이 일어나는 경우 이를 반공변성(Contravariance)이라고 한다.
