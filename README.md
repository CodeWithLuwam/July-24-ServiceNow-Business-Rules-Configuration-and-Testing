# July-24-ServiceNow-Business-Rules-Configuration-and-Testing

Business Roles Navigation: <br>
All > System Definition > Business Rules <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Business%20Rules%20Navigation.png?raw=true) <br>
Click New in the Business Rules table to create a New Business Rule <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Click%20New%20in%20the%20Business%20Rules%20table.png?raw=true) <br>

---
A short cut to build it is by going to the table you are currently working with, right click on the column header, hover on Configure  then click Business Rules. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Different%20option%20to%20Configure%20Business%20Rules.png?raw=true)
It will open up a table with all the Business Rules tied to the table. <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Business%20Rules%20tied%20up%20to%20the%20table.png?raw=true) <br>
![](https://github.com/CodeWithLuwam/July-24-ServiceNow-Business-Rules-Configuration-and-Testing/blob/main/Images/Asset%20Recovery%20Request%20Business%20Rule%20table.png?raw=true) <br>

---
Scenario: <br>
At DXC Tech, you're part of the IT Asset Management team. When a device is returned, you need to document what kind of device it is, who returned it, and confirm that asset tracking information is accurate. To help execute this, you'll automate two things: <br>
- A reminder to double-check the asset tag when a laptop is returned <br>
- A description that includes the employee's name <br>

TASK:<br>
**Business Rule 1: Create a Reminder Message** <br>
&emsp;Create a Business Rule that displays:<br>
&emsp;"Please ensure the asset tag number is correct for all laptops." when Asset Type is Laptop and the Asset Tag field is not empty<br>
**Business Rule 2: Auto-fill Description**<br>
&emsp;Create another Business Rule that fills in the Short Description with "Asset recovery initiated for [Employee Name]" only if it's empty <br>
**Test Your Work** <br>
Create a new Asset Recovery Request<br>
