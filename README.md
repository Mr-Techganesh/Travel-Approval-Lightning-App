# Travel-Approval-Lightning-App

## Business Requirements

> Your organization has decided to implement a custom travel approval app. Up until now, you had a travel approval process in place based on emailing spreadsheets. It had no central repository or enforcement of the process, resulting in the inability to report on travel approval activities across the organization. You need to create an application that meets these requirements
Your organization has decided to implement a custom travel approval app. Up until now, you had a travel approval process in place based on emailing spreadsheets. It had no central repository or enforcement of the process, resulting in the inability to report on travel approval activities across the organization. You need to create an application that meets these requirements



-  Each employee must submit an electronic request in the system for future travel.

-  Each request includes a list of estimated expenses for airfare, hotel, rental car, and so on.

-  Each request must be approved by the employee’s manager, and all out-of-state travel must be approved by a travel coordinator.

-  Managers need reports and dashboards to track key travel request trends and KPIs.

-  In addition, employees and managers must be able to access their travel requests, approvals, and dashboards via mobile devices.

  

## Process in the Project

-  Build a Lightning app, add tabs, and customize page layouts.
-  Create custom objects and fields for the app.
-  Define relationships between objects.
-  Import data and test the app.

## Data Modeling
*Create Custom Objects and Fields:*

Creating your organization’s travel approval app is to create the data model. The first object to create is the Department object. This object stores information about your departments such as name and cost center code.

*Department Object*
-  From Setup, click Object Manager.
-  Click Create, then Select Custom Object

 *Fields & Relationships of Department Object*
-  Department Code
-  Type: [Text]

*Create a Travel Approval Object*
-  Data Type: Auto number

*Fields & Relationships*

*Purpose of Trip*
-  Data Type: text
-  Status  
*data type: Picklist*

*values:*

-  New
-  Submitted
-  Pending Approval
-  Approved
-  Rejected
-  Draft
-  Create the Trip Start Date field with a Date data type.
-  Create the Trip End Date field with a Date data type.
-  Create the Out-of-State field with a Checkbox data type.
-  Create the Destination State field with a Text data type

Create the Department field with a Lookup Relationship data type, then select Department for the Related To field

*Expense Item Object*
-  Data Type AUTO NUMBER
-  Format E-{00000}
*Fields and Relationship of Expence object*
 -  Amount
-  Currency.

*Expense Type  Pick List*
-  Airfare
-  Hotel
-  Rental car
  -  Meals
-  Other

*Create the Travel Approval field*

Select Master-Detail Relationship data type, click Next.
Select Travel Approval from the Related To menu.

## Customize the User Interface for a Travel Approval App

*Create a User*
-  Profile System Administrator
-  Enable Approval Settings
 -  select your user account  Set your manager as Eric Executive

*Create and Customize a List View*

select the Travel App and select the Travel Approvals tab.
1.	Select record TA-00001 under All LIST VIEWS.
2.	Click the gear icon, then select Edit Object. This loads the object configuration page for the Travel Approval object. 
3.	Click Search Layouts. Click the down arrow for the Default Layout and select Edit from the dropdown.
4.	Use the Add arrow to move these fields into the Selected Fields column, in order.
•	Purpose of Trip
•	Department
•	Status
•	Destination State
•	Trip Start Date
•	Trip End Date 
5.	navigate back to the Travel App and click the Travel Approvals tab..
6.	Click Recently Viewed and select the All list view.
7.	Click the gear icon then select Select Fields to Display from the dropdown.
8.	Use the Add arrow to move these fields to the Selected Fields column, in order.
•	Department
•	Created By
•	Status
•	Trip Start Date
•	Trip End Date

*custom list view:*

In this scenario, you create a list view with a filter to show all out-of-state travel requests that have not been approved or rejected. This way you can see exactly what approvals are still outstanding.
1.	Click the List View gear icon and select New option.
2.	Name the new list view Open Out of State Travel Requests and select All users can see this list view.
3.	Click Save.
4.	Click Add Filter and enter these details:
•	Field: Out-of-State
•	Operator: equals
•	Value: True
5.	Click Done.
6.	Click Add Filter again and enter these details:
•	Field: Status
•	Operator: not equal to
•	Value: Approved, Rejected
7.	Click Done.
8.	Click Save.
9.	Click the gear icon and select Select Fields to Display.

    ![image](https://github.com/strganeshmoorthy/Travel-Approval-Lightning-App/assets/117075085/12dbe7b6-bd30-4f51-ac1a-7ba080f76e10)

 
11.	Use the Add arrow to move the following fields to the Visible Fields column, in order.
    
•	Department
•	Created By
•	Status
•	Destination State
•	Trip Start Date
•	Trip End Date
13.	Click Save.
Keep up the great work! Move on to the next step and customize the page layout of the Travel Approval 


## Customize the Travel Approval Object Page Layout

*Customize a Page Layout*

1.	Travel Approvals tab and open TA-00001.
2.	Click   and then select Edit Page. 
3.	Left-click once in the middle of the form to select it. You should see a light blue border around the form. On the right-hand side, click Travel Approval Layout (previewed). 
4.	Drag Section from the top pane to the lower pane directly below the Information section.
5.	Name the section Trip Info
6.	Drag Purpose of Trip, Trip Start Date, and Trip End Date 
7.	Drag Out-of-State and Destination State from the Information section
8.	Drag the Department field from the left-hand column of the Information section to the right-hand column.

*Edit the Expense Item Related List*

Related lists can be added to any Salesforce page they are related or linked to.

1.	From Page Layouts in the Object Manager, select Travel Approval Layout. Scroll down to the Expense Items related list. Click the wrench icon in the header tab. 
2.	Move the Expense Type and Amount fields from Available Fields to Selected Fields.
3.	Click OK. Click Yes if you’re asked if you want to Overwrite Users’ Related Lists Customizations.
4.	Click Save.
5.	Navigate back to a Travel Approval record and look at the related lists. You should see the extra columns you added to the expense item related list.
   
*Enable Chatter Feed Tracking*

Enable Chatter feed tracking on the Travel Approval object.
1.	From Setup, enter Feed Tracking in the Quick Find box, then select Feed Tracking.
2.	In the list of available objects, click Travel Approval.
3.	Select Enable Feed Tracking.
4.	Select these fields:
o	Destination State
o	Status
5.	Click Save

## Add Business Logic to a Travel Approval App

*Validation Rules*

 Validation rules let you set up business-specific criteria to prevent users from saving invalid data in one or more fields. A validation rule evaluates a formula when a record is saved. If a rule’s criteria aren’t met, users see a custom error message and the record doesn’t save. If a rule’s criteria are met, the record saves. Use validation rules to improve data quality by applying conditions, ensuring proper formatting, and enforcing consistency.
 
1.	Select Travel Approval to open the configuration page for the Travel Approval object.
2.	Click Validation Rules.
3.	Click New. 

* Parameter Value*



| Rule Name | Trip end date after start date |
| --------- |------------------------------- |
| Active | Make sure to keep this selected/checked |
| Condition Formula | 	```  Trip_End_Date__c < Trip_Start_Date__c ```  |
| Error Message |  Trip end date must be greater than or equal to start date |
| Error Location | Select Field and pick |





![image](https://github.com/strganeshmoorthy/Travel-Approval-Lightning-App/assets/117075085/1fedc22f-f662-46fa-8233-dddcca98715c)

  

*Create a Roll-Up Summary Field*

 Travel Approval object that automatically sums up the total amount of expenses from the related Expense Items. Salesforce has a field called a roll-up summary field that provides this functionality.
1.	From the Travel Approval object, select Fields & Relationships.
2.	Click New.
3.	Select the Roll-Up Summary data type.
4.	Click Next.
5.	Enter the following values for the field details:
   
Field Label: Total Expenses

Configure the roll-up calculation




| Summarized Object | Expense Items |
| ----------------- | ------------- |
| Roll-Up Type |  SUM |
| Field to Aggregate | Amount |
| Filter Criteria | All records should be included in the calculation |

 

*Formula Fields*

create a field on the Travel Approval object that shows a visual indicator (that is, image file) based on the value of the Status field. For example, one image displays for Rejected approvals and a different image for Approved approvals. This provides a quick and simple way for users of the system to get an indicator of the status of a travel approval.




| Parameter | Value |
| --------- | ------ |
| Name| StatusImages  (Important: there are no spaces, and the S and I are capitalized) |
| File | StatusImages.zip |
| Cache-Control |  Public |

 

*Add a Field*

Next, create a new field on the Travel Approval object to show an image based on the Status field. Salesforce has a formula field data type that can be used for this.
1.	Click the   icon next to the Object Manager tab. This provides a shortcut to the Object Manager for the recent objects you have edited.
2.	Select Travel Approval
 
3.	Select Fields & Relationships.
4.	Click New
5.	Select Formula data type.
6.	Click Next.
7.	Enter the following values:
•	Field Label: Status Indicator
•	Field Name: Status_Indicator (This automatically gets sent when you tab out of the Field Label field)
•	Formula Return Type: Text
8.	Click Next.
9.	Copy and paste the following formula into the formula editor.

```
IF( ISPICKVAL( Status__c , 'Approved') , IMAGE("/resource/StatusImages/thumbs-up.png", "Accepted", 20, 20),
IF ( ISPICKVAL( Status__c , 'Rejected'), IMAGE("/resource/StatusImages/thumbs-down.png", "Rejected", 20, 20),
IMAGE("/resource/StatusImages/draft.png", "In-Process", 20, 20)))
```

## Flow

The last business rule functionality to implement before testing your application is a rule to set the Out-of-State checkbox field on the Travel Approval object if out-of-state travel has been chosen. Salesforce offers workflow capabilities that provide a declarative, drag-and-drop design environment to build our business process logic
•	Salesforce Flow—The product that encompasses building, managing, and running flows and processes.
•	Flow Builder—A point-and-click tool for building flows.
•	Flow—An application that automates a business process by collecting data and doing something in your Salesforce org or an external system.

*New Flow.*

Select Record-Triggered Flow then click Create.

ParameterValue:

| Object | Travel Approval |
| -------| ----------
| Configure Trigger | Trigger the flow when: A record is created or updated |
| Condition Requirements |  None |



Optimize the Flow For Fast Field Updates



*Add a Decision Element*



| Parameter | Value |
| --------  | ----- |
| Label |  Yes Out of State |
| Outcome API Name | Yes_Out_of_State (This automatically gets set when you tab out of the Label field) |
|Condition Requirements to Execute Outcome | All Conditions Are Met (AND) |
| Resource | Record > Destination State |
| Operator | Does Not Equal |
| Value | TX |



When to Execute the Outcome	Only if the record that triggered the flow to run is updated to meet the condition requirements
	



| Parameter | Value |
| --------  | ----- |
| Label |  In State |
| Outcome API Name | In_State (This automatically gets set when you tab out of the Label field) |
|Condition Requirements to Execute Outcome | All Conditions Are Met (AND) |
| Resource | $Record > Destination State |
| Operator | Equals |
| Value | TX |

When to Execute Outcome	Only if the record that triggered the flow to run is updated to meet the condition requirements


Create an Action for the Flow Using Update Records Elements
1.	From the left-hand column, the flow toolbox, drag an Update Records element onto the flow screen.
2.	Set the parameters for the element

## BLOCK DIAGRAM:

 ![image](https://github.com/Mr-Techganesh/Travel-Approval-Lightning-App/assets/117075085/0834fa11-b202-44fe-8c38-3fa636b9a965)


1.	Click Save.
2.	Flow Label: Out of State Travel Flag. Flow API Name will auto populate to Out_of_State_Travel_Flag. Leave Description blank and advanced settings as is.
3.	Click Save. 
 

## Approval Process

In this section, you create an approval process that all travel approvals must follow. We keep it simple and use the following logic.

All travel approvals are sent to the employee’s direct manager for approval.
If the trip is out of state, the approval is also sent to a travel coordinator for approval. If not out of state, this step is skipped.

1.	Click   and select Setup.
2.	Select Process Automation | Approval Processes (or use the Quick Find and search for Approval Processes). 



*Parameters*




| Parameter |  Value |
| --------- | ------ |
| Name | Travel Approval Request |
|Unique Name  | Travel_Approval_Request (This automatically gets sent when you tab out of the Name field) |
| Approval Assignment Email Template | 	Leave blank |




Add the Submit for Approval button and Approval History related list to all Travel Approval page layouts	Leave this selected/checked
Use Approver Field of Travel Approval Owner

Specify Entry Criteria	Use this approval process if the following: criteria are met.



| Parameters | Values |
| ---------- | ------ |
| Field: | Travel Approval: Total Expenses |
| Operator | greater than |
| Value |  0 |



*Select Approver*	 

1.  Automatically assign an approver using a standard or custom hierarchy field
1.  Select Manager from the option list


*Create an Approval Step for Out-of-State Travel*


*details*


| Parameter | Value |
| --------- | ----- |
| Name |  Travel Coordinator Approval |
| Unique Name | Travel_Coordinator_Approval (This automatically gets set when you tab out of the Name field) |
| Step Number | 2 |




*Add Logic*

Next, add logic to set the status of the approval request based on if it was Approved or Rejected. We do this by creating a Final Approval action and a Final Rejection action. Let’s start by creating an action if the request was approved by all approvers.

1.	Click Add New in the Final Approval Actions area of the approval process form.
2.	Select Field Update from the dropdown list.
 
3.	Enter the following values.


   

| Parameter | Value |
| --------- | ------|
| Name | Set Status to Approved |
| Unique Name | Set_Status_to_Approved (This automatically gets sent when you tab out of the Name field) |
| Field to Update | Status |





set the status value to Rejected if any approver rejects the travel approval request. 

1.	Click Add New in the Final Rejection Actions area of the approval process form.
2.	Select Field Update from the dropdown list.  
3.	Enter the following values.


   
   
| Parameter |	Value |
| --------- | --------|
| Name | Set Status to Rejected |
| Unique Name |	Set_Status_to_Rejected (This automatically gets sent when you tab out of the Name field) |
| Field to Update | Status |
| Picklist Options | Select A specific value and select Rejected from the dropdown list. |


5.	Click Save.
6.	Click Activate.
7.	Select OK in the popup window to confirm activation. Your approval process should now have the Active flag checked.  

set the status value to Rejected if any approver rejects the travel approval request. 

1.	Click Add New in the Final Rejection Actions area of the approval process form.
	
4.	Select Field Update from the dropdown list.
   
5.	Enter the following values.



   

| Parameter | Value |
| --------- | ----- |
| Name | Set Status to Rejected |
| Unique Name | Set_Status_to_Rejected (This automatically gets sent when you tab out of the Name field) |
| Field to Update | Status |
| Picklist Options | Select A specific value and select Rejected from the dropdown list.|




4.	Click Save.


## Add Reports and Dashboards to a Travel Approval App

*Create a Dashboard*

You can take your analysis to the next level by placing your reports on a Salesforce dashboard for quick and easy viewing. A dashboard provides an interactive visual display of key metrics and trends. Multiple dashboard components can be shown together on a single dashboard layout, creating rich visual displays of multiple reports that have a common theme.

1.	Click the Dashboards tab.
2.	Click New Dashboard. 






3.	Enter the following values


   

| Parameter | Value |
| --------- | ----- |
| Name | Travel Requests Dashboard
| Description | Leave blank
| Folder | Private Dashboards
	
	



4.	Click Create.  You can now add reports to your dashboard and move them on to different 
5.	sections of the dashboard. You can also stretch the components across the grid to have the exact layout of components you need for your dashboard.
6.	Click + Component.
7.	Click the Travel Request by Department report and click Select. You are presented with options to configure this component for the dashboard.
8.	Make sure the Y-Axis is set to Department and the X-Axis is set to Record Count.




## Dashboard View 

   ![Screenshot 2023-12-23 235731](https://github.com/Mr-Techganesh/Travel-Approval-Lightning-App/assets/117075085/d9e890e1-2257-4163-99bb-3bfb094e4538)




## Report View


![report view](https://github.com/Mr-Techganesh/Travel-Approval-Lightning-App/assets/117075085/c5de2fd7-d929-4fd2-9aaa-21800ef16781)



## Department View


![dept view](https://github.com/Mr-Techganesh/Travel-Approval-Lightning-App/assets/117075085/a287ba05-9489-4f2c-8f49-8c837b89c2f2)




## Travel Approval View

![travel app view](https://github.com/Mr-Techganesh/Travel-Approval-Lightning-App/assets/117075085/5c9a4612-3e7c-46ab-b999-1fec9722c9cc)







