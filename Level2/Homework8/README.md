# #8 Data Types and Structures

* Trailhead - ***Developer Console Basics*** - *!only first two items*

 Practical Task 2: Create a function that returns the name of the winner in a fight between two fighters. Each fighter takes turns attacking the other and whoever kills the other first is victorious. Death is defined as having health <= 0. Each fighter will be a Fighter object/instance. Both health and damagePerAttack will be integers larger than 0. You can mutate the Fighter objects.

`Fighter` object default implementation:
```java
public class Fighter {
    public String name;
    public Integer health;
    public Integer damagePerAttack;

    public Fighter(String name, Integer health, Integer damagePerAttack) {
        this.name = name;
        this.health = health;
        this.damagePerAttack = damagePerAttack;
    }
}
```

The function that returns a name of a winner:
```java
public static String mortalCombat(Fighter f1, Fighter f2) {
        Integer scoreF1 = f1.health / f2.damagePerAttack;
        Integer scoreF2 = f2.health / f1.damagePerAttack;
        return scoreF1 >= scoreF2 ? f1.name : f2.name;
}
```