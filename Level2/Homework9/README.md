# #9 Data Structures and Algorithms

***Practical Task1***: Get unique values in list.  
***Practical Task2***: Get Contact by Name.  
***Practical Task3***: Get Opportunity with the biggest amount.  
***Practical Task4***: Write a function that takes a number and returns a list of its digits.  

[Trailhead](https://trailhead.salesforce.com/en/content/learn/modules/object-oriented-programming-for-admins/define-sets-and-maps?trail_id=build-apex-coding-skills)

### Source
```java
public class ExtensiveClass {
    public static Set<Integer> getUnique(List<Integer> l) {
        return new Set<Integer>(l);
    }

    public static Contact getContact(String name) {
        SObject findContact = [SELECT Id, Name FROM Contact WHERE Name = :name Limit 1];
        return (Contact) findContact;
    }

    public static Opportunity getCostliestOpp() {
        SObject richestOpp = [SELECT Id, Name, Amount From Opportunity WHERE Amount > 0 ORDER BY Amount DESC LIMIT 1];
        return (Opportunity) richestOpp;
    }

    public static String[] numToList(Decimal num){
        return String.valueOf(num).remove('.').split('');
    }
}
```

<details>
<summary>Additional Task</summary>
Develop <i>Stack</i> and <i>Queue</i>
</details>