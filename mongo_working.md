## create database

MongoDB use DATABASE_NAME is used to create database. The command will create a new database if it doesn't exist, otherwise it will return the existing database.

Syntax
Basic syntax of use DATABASE statement is as follows −

use DATABASE_NAME


## import data from csv
```
 mongoimport -d mydb -c collectionName --type csv --file myfile.csv --headerline

```

## day of week

```
db.bankthrift.find().forEach(function(item){var mydate = item.pitdate.split('/'); var dayofweek = ( (new Date(mydate[2], mydate[0] - 1 , mydate[1] )+ '' ) .split(' ')[0] ); db.bankthrift.update({_id: item._id}, {$set: {day: dayofweek}})   } )

```