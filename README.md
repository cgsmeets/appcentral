# Salesforce App

DOASPAS Objects
 - SAJ_Analyze_Job__c
 - SAJ_Analyze_Job_Assignment__c
 - SAJ_Analyze_Job_Summary__c
 - SAJ_Analyze_Result__c
 - SAJ_DEUS_Analyze_Jobs

Assign Permissionset
sfdx force:user:permset:assign -n SAJ_DEUS_Analyze_Jobs -u <ORG>

Import data:
sfdx force:data:tree:import -f ./data/SAJ_Analyze_Job__c-SAJ_Analyze_Job_Assignment__c.json -u <ORG>

Extract data: 
sfdx force:data:tree:export -q "select name, (SELECT Id, Name, SAJ_Environment__c, SAJ_Operation__c, SAJ_App__c, SAJ_Analyze_Job__c FROM Analyze_Job_Assignments__r) from SAJ_Analyze_Job__c" -u <ORG>
