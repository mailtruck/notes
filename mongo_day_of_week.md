# mongo day of week

```
db.bankthrift.find().forEach(function(item){var mydate = item.pitdate.split('/'); var dayofweek = ( (new Date(mydate[2], mydate[0] - 1 , mydate[1] )+ '' ) .split(' ')[0] ); db.bankthrift.update({_id: item._id}, {$set: {day: dayofweek}})   } )

```