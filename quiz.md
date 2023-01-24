# Polymorphism

1. What does the ___word___ 'polymorphism' mean?

It means that multiple different objects or classes share a common interface that can be consumed by users of the objects or classes.

2. What does it mean when we apply polymorphism to OO design? Give a simple Java example.

In OO design, polymorphism refers to subtype polymorphism where a method or attribute can accept many different objects that conform to the same interface.

```java
public static void printItems(Iter<Object> objects) {
	for (Object object : objects) {
		System.out.println(object)
	}
}
```

(XXX not sure this shows much design?)

3. What can we use to implement polymorphism in Java?

Interfaces, superclasses, abstract base classes, overloaded methods.

4. How many 'forms' can an object take when using polymorphism?

Unbounded generally, but Java has 'sealed' classes which can limit polymorphism.

5. Give an example of when you could use polymorphism.

A base class could have a `String convertToJSON()` method, and each derived class could provide its own implementation of it.


# Composition and Aggregation

6. What do we mean by 'composition' in reference to object-oriented programming?

Composition means that objects contain instances of other objects that implement the containing object's behaviour.

7. When would you use composition? Provide a simple example in Java.

You would use composition to share implementation of a behaviour between two classes when it is not appropiate to have a common superclass.

```java
public class NamedThing {
  private final String name;
  public NamedThing(String name) { this.name = name }
  public String getName() { return name }
  public void callName() { System.out.println(name) }
}
```

Then both Person and Pet can contain a NamedThing and use that to provide `callName` but without Person and Pet inappropiately sharing a parent class. 

8. Give a difference between composition and aggregation?

In composition, the contained objects are considered 'owned' by their container and don't make sense to have a lifetime beyond that of their container.  In an aggregation, the objects may have some use outside the lifetime of the container.

9. What is/are the advantage(s) of using composition/aggregation?

They allow reuse of functionality without requring inheritance to be used.  They allow encapsulation of the implementation of the behaviour, enhancing separation of concerns, and allowing possibilities like inversion of control where the contained object can be swapped for one with the same interface.

10. When using composition, when an object is destroyed, what happens to all the objects it is composed of?

The contained objects are also destroyed.

11. When using aggregation, when an object is destroyed, what happens to all the objects it is composed of?

The contained objects may not be destroyed if they are used outside of the aggregation.
