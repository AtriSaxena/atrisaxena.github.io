---
title: "Use Salesforce python library to Edit, Update, View Salesforce Object"
categories:
  - Tutorial
classes: wide
tags:
  - Salesforce
  - Python 
  - Developement
---


<p align="center">
  <img height="300px" width="300px" src="https://i.pinimg.com/originals/9d/be/13/9dbe13dfd87ef4f36fe1d4671dfa9ddc.png">
</p>
## Salesforce Python Library

Salesforce python library "simple_salesforce" uses Salesforce REST API to view, edit, delete, create records. You can also write custom SOQL(Salesforce Object Query Language) and run to get records from your salesforce organization. 

In this tutorial I will discuss: 

1. Installing "simple_salesforce" python library.
2. Create a record.
3. View/get some record.
4. Update a record.
5. Delete a record. 
6. Run custom SOQL query. 

Let's start

### 1. Installing "simple_salesforce" python library

To install "simple-salesforce" python library to need to have python install on your system. To check if python is installed on your system. 
Open command prompt(cmd) and type "`python --version`", if you see output with python version you are good to go else you can install python from [python.org](https://python.org)

After successfully installing python run `pip install simple-salesforce` this install the simple-salesforce package. 

- ### Authentication: 

<p align="center" height="300px" width="300px">
  <img src="https://i.imgur.com/wVg03nc.png">
</p>

For connecting this python package to your salesforce organization there are two methods: 
- The first is to simple pass the domain of your salesforce instance and an access token straight to `Salesforce()` 

For example: 

```
from simple_salesforce import Salesforce
sf = Salesforce(instance='na1.salesforce.com', session_id='')
```

- Second method is to pass the username, password and the security token. 

For example: 

```
from simple_salesforce import Salesforce
sf = Salesforce(username='myemail@example.com', password='password', security_token='token')
```

And if you like to enter the sandbox, simple add the `domain='test'` to the Salesforce() function. 

For Example: 

```
from simple_salesforce import Salesforce
sf = Salesforce(username='myemail@example.com', password='password', security_token='token', domain='test')
```
Hint: To get your security token. Go into Profile setting in your salesforce and click on Reset Security token. You will get your token on your registered Email id. 


### 2. Create a record

To create a new record you need to mention the Salesforce Object. For example we can take `Contact` object in salesforce and create a record in `Contact` object. 

For Example: 

```
sf.Contact.create({'LastName': 'Kumar', 'Email': 'example@example.com'})
```

Using the Authentication object of Salesforce() function we need to pass the dictionary of the data to create() functions. This functions returns the dictionary value if it success or failure such as `{u'errors': [], u'id': u'003e0000003GuNXAA0', u'success': True}` with id of create record. 

### 3. View/get some record

To read a record from an object like the previous record we have created we need to know the id of the record or the External ID created which is unique to the object. 

For Example: 
```
contact = sf.Contact.get('003e0000003GuNXAA0')
```

To get a dictionary with all the information regarding that record, using a custom field that was defined as External ID:

```
contact = sf.Contact.get_by_custom_id('My_Custom_ID__c', '22')
```

### 4. Update the record: 

To the Change the contacts last name from `Kumar` to `Sharma` and also add a First name i.e., to upsert (update and insert) we do that as following: 

```
sf.Contact.update('003e0000003GuNXAA0',{'LastName': 'Sharma', 'FirstName': 'Rahul'})
```

### 5. Delete the record:

For delete a Record in Salesforce you can just call delete by passing the record id. 

```
sf.Contact.delete('003e0000003GuNXAA0')
```


### 6. Running SOQL Query

It's also possible to write select queries in Salesforce Object Query Language (SOQL) and search queries in Salesforce Object Search Language (SOSL).

```
sf.query("SELECT Id, Email FROM Contact WHERE LastName = 'Jones'")
```
This query returns the dictionary with single record and `nextRecordsUrl` to your query result, such as  `"nextRecordsUrl" : "/services/data/v26.0/query/01gD0000002HU6KIAW-2000"`, you can pull the additional results with either the ID or the full URL (if using the full URL, you must pass 'True' as your second argument)

```
sf.query_more("01gD0000002HU6KIAW-2000")
sf.query_more("/services/data/v26.0/query/01gD0000002HU6KIAW-2000", True)
```
or a more convenient method which returns all the records of the query using the query_all() function as follows:

```
sf.query_all("SELECT Id, Email FROM Contact WHERE LastName = 'Jones'")
```

SOSL queries are done via:

```
sf.search("FIND {Jones}")
```
Search will return `None` if there are no records found else return dictionary of record.


More details about SOQL & SOSL query is available on the [Salesforce Developer Website.](http://www.salesforce.com/us/developer/docs/soql_sosl/index.htm)



## Example of running SOQL Queries and Save result in CSV

I have written a small code, because many times you will face problem you don't have record ids to update the record. So, using this code you can find the record id using some unique value is known to you. 

So, the very first step is to create a CSV file with Columns filters you want to apply in SOQL query.  

Than create an Auth.py file like below with all details. 

<script src="https://gist.github.com/AtriSaxena/ae4a664caf2fcc7860c37367857b4698.js"></script>

In this next file, you can just pass the arguments in the file to get the Id of records and below script will return a csv file named `output.csv` with record ids. 


<script src="https://gist.github.com/AtriSaxena/7afefab113454c829971d03c15fb070e.js"></script>


For Example: 

```
python Get_ID.py --object Object1 --columns "Id, col1, col2, col3" --where_field Name --csv_file myfile.csv --csv_field_map NameofPerson
```

Argument named 

- --object: Object name of the record you want. 
- --columns: Columns value from the object you want. 
- --where_field: On which field you want to apply filter. 
- -- csv_file: Input csv file which contains the where_field values.
- -- csv_field_map: Field Name defined in csv file for where_field mapping.

You can modify the code according to your problem and see the Salesforce developer to find more about SOQL. It actually helped me to update the records in bulk and it might help you also to make things do faster. 


<p align="center" >
  <img height="350px" width="300px" src="https://media.makeameme.org/created/may-the-salesforce.jpg">
</p>
