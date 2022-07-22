# #10 SOQL & DML

→ Trailhead - Developer Console Basics - remaining items  
→ Trailhead - SOQL for Admins  
→ Trailhead - Apex Basics and Database  
→Documentation - SOQL and SOSL Reference guide - SOQL 
`SELECT` syntax, Relationship Queries  
→ Documentation - Apex DML Operations  

→ <u>Practical Task</u>: Write a method `updateOpportunityStage`, which takes <u>two</u> `String` parameters -` stageNew` and `stageOld`, queries all **Opportunity** records, which have `StageName = :stageOld`, and updates them with `stageNew`, returning the list of updated **Opportunities**. This method should check if `stageNew` and `stageOld` are valid picklist values for **Opportunity**. `StageName` - use the following code to get the list of available picklist 
values:
```apxc
List<Schema.PicklistEntry> opportunityStages = 
Opportunity.StageName.getDescribe().getPicklistValues();
```

#### Source:
```csharp
public static void updateOpportunityStage(String stageOld, String stageNew) {
        if (!IsAllOpportunityStages(stageNew, stageOld)) {
            throw new ExternalObjectException('Invalid stage for Opportunity');
        }

        Opportunity[] oldStagedOpps = [SELECT Id, Name, StageName FROM Opportunity WHERE StageName = :stageOld];
        for (Opportunity opp : oldStagedOpps) {
            opp.StageName = stageNew;
        }
        update oldStagedOpps;
    }

    private static Boolean IsAllOpportunityStages(String stageNew, String stageOld) {
        List<Schema.PicklistEntry> oppStages = Opportunity.StageName.getDescribe().getPicklistValues();

        // Whether there are such pick lists like stageNew and stageOld
        Boolean stageNewFound = false, stageOldFound = false;
        for (PicklistEntry pickList : oppStages) {
            if (pickList.getLabel() == stageNew) {
                stageNewFound = true;
            } else if (pickList.getLabel() == stageOld) {
                stageOldFound = true;
            }

            // if both are found, step out from the loop
            if (stageOldFound && stageNewFound) {
                return true;
            }
        }
        return false;
    }
```