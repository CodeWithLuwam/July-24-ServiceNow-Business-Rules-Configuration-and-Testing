# July-24-ServiceNow-Business-Rules-Configuration-and-Testing

Scenario: <br>
At DXC Tech, you're part of the IT Asset Management team. When a device is returned, you need to document what kind of device it is, who returned it, and confirm that asset tracking information is accurate. To help execute this, you'll automate two things: <br>
- A reminder to double-check the asset tag when a laptop is returned <br>
- A description that includes the employee's name <br>

TASK:<br>
**Business Rule 1: Create a Reminder Message** <br>
&emsp;Create a Business Rule that displays:<br>
&emsp;"Please ensure the asset tag number is correct for all laptops." when Asset Type is Laptop and the Asset Tag field is not empty<br>
**Business Rule 2: Auto-fill Description**<br>
&emsp;Create another Business Rule that fills in the Short Description with "Asset recovery initiated for [Employee Name]" only if it's not empty <br>
**Test Your Work** <br>
Create a new Asset Recovery Request<br>

---
**Business Rule 1: Create a Reminder Message** <br>

**When to run** tab:
- Asset Type is Laptop
- AND
- Asset Tag is not empty

Both conditions must be true.

- We also check off Insert and Update 
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/When%20to%20run%20tab-%20%20Business%20Rule.png?raw=true) <br>

**Actions** tab: <br>

Set up an **Add Message** action so that when a user is returning a laptop, a pop-up appears with the message:
> Please ensure that the asset tag number is correct for your laptop.

**Conditions for the message to appear**:
1. Asset Type is Laptop.
2. Asset Tag field is not empty.

Do not place this in the Short Description field — use the **Add Message** option to display it as a pop-up. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Actions%20tab%20-%20Business%20Rule.png?raw=true)

---

**To test**: <br>
1. Navigate to the module we created: <br>
&emsp;**All > DXC Technology Device > Device Inventory** <br>
2. Perform the actions needed to meet the trigger conditions (**Insert** or **Update**).  <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Open%20an%20Existing%20Record.png?raw=true) <br>
3. For this test, update a form to trigger the conditions.  <br>
( Reminder Message Appears )
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Task%20Message%20Pops%20Up.png?raw=true)

---

**Business Rule 2: Auto-fill Description**<br>
We are working with the **Employee** field, and the message should only display if this field is not empty. <br>
We are still checking the **Insert** and **Update** boxes so the action runs on both record creation and modification. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/When%20to%20run%20tab%20for%20Business%20Rule%202%20.png?raw=true) <br>

We now check the Advanced box, which makes the Advanced tab appear. <br>
We will skip the Actions tab because the script in the Advanced tab will serve as our action. <br>

In the script: <br>
- We’re creating a **Business Rule** that runs when the record is inserted or updated.
- The script first checks if the **Short Description** field (`current.short_description`) is empty.
- If it’s empty, it retrieves the **Employee** field’s display value (`current.employee.getDisplayValue()`), stores it in the `empName` variable, and sets the **Short Description** to: <br>
`Asset recovery initiated for [Employee Name]` <br>
- This ensures that the short description is automatically populated based on the employee name whenever a record is created or updated, but only if it was blank before. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Business%20Rule%202%20Advanced%20tab.png?raw=true)

---
---
---
**Business Rules Navigation**: <br>
1. Go to **All > System Definition > Business Rules**. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Business%20Rules%20Navigation.png?raw=true) <br>
2. Click **New **in the Business Rules list to create a new Business Rule. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Click%20New%20in%20the%20Business%20Rules%20table.png?raw=true) <br>

**Shortcut**: <br>
If you’re already on the table you’re working with, right-click the column header, hover over **Configure**, and select **Business Rules**. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Different%20option%20to%20Configure%20Business%20Rules.png?raw=true) <br>
This will open a list of all Business Rules tied to that table.. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Business%20Rules%20tied%20up%20to%20the%20table.png?raw=true) <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Asset%20Recovery%20Request%20Business%20Rule%20table.png?raw=true) <br>

