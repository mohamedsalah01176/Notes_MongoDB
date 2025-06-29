# Notes_MongoDB

// many entity in No SQL from SQL Database
/*

collection => table
document = row

we use json (JSON.stringfy(data)) in requestan && response => because if occur bad network (serailzation)
mongo save data as Bjson => to improve response time

we can write javascript

engin for chorom && edge=> V8
engine for fire Fox => spider Monky => MongoDB
============ commands

show dbs
use NameDB
db.createCollectiom("nameDB")
show collection


=============== CRUD

db.nameCollection.insert()
db.nameCollection.insertOne()
db.nameCollection.insertMany()

to modify default id => db.nameCollection.insert(_id:1,....)
if put spicific field 1 => other field will take 0 and oppisite 
db.nameCollection.findOne()
db.nameCollection.find({condition},{projection})
db.nameCollection.find({age:20},{name: 1 || true , _id: 0 || false}) // _id => default true

projection => we use it to show spicific field in row (spicif column)
condition => { age:20 , name:"mohamed" } 

db.nameCollection.find({age:20,age:12}) // it will do overrride and return field with age 12



1 ==== copmparison operator (gt , gte , lt ,lte)
db.nameCollection.find({age:{$gte:21}})
db.nameCollection.find({age:{$in:[27,30]}}) // at the same or operator




2 ==== Logical operator 
db.nameCollection.find({$and:[{name:"mohamed",age:30}]})
db.nameCollection.find({$and:[{name:"mohamed",age:30,age:20}]}) // it will not return  field becase we do not have age in on efield 20 and 30
db.nameCollection.find({$or:[{name:"mohamed",age:30,age:20}]}) // it will return all field with name is mohamed and age is 30 or 20



3 ==== array operator 

db.nameCollectio.find({courses:"js"}) // by default it will cc=heck in array about js



4 ==== element operator 
-exist
db.nameCollection.find({age:{exist:true}})

-type
db.nameCollection.find({name:{type:string}})




5 ==== embeded operator
db.nameCollection.find({"address.city":"cairo"}) // return all field with address cairo
db.nameCollection.find({address.city:"cairo"}) // error => this syntax no use in key object
db.nameCollection.find({},{"address.city":"cairo"}) // return all city field 
db.nameCollection.find({},{address{city:"cairo"}}) // return address that have {city:"cairo"}




// loop
db.nameCollection.find({}}).forEach((inst)=>{
    print(`Name is ${inst.name}`)
})

db.nameCollection.find({Salary:{$exist:true}}}).forEach((inst)=>{ do condition with loop
    print(`Name is ${inst.name}`)
})





// update
- add and update field (column)
db.nameCollection.updateOne(condition,updateCommand,options)
db.nameCollection.updateOne({name:"ahmed"},{$set{salary:3000}}) // one Field
db.nameCollection.updateMany({name:"ahmed"},{$set{salary:3000,address:{city:"Giza"}}}) // All Fields

- remove (column)
db.nameCollection.updateOne({name:"ahmed"},{$unset{salary:""}}) // one Field

-rename
db.nameCollection.updateOne({name:"ahmed"},{$rename{salaryBD:"salary"}}) // rename column 

// modefiy on behavior on update
db.nameCollection.updateOne({name:"khaled"},{$set{salaryBD:1000},{upsert:true}}) // check about name if not found insert that name

// change object
db.nameCollection.updateMany({_id:5},{$set:{"address.city":"Giza"}}}) 
db.nameCollection.updateMany({_id:5},{$unset:{"address.city":"Giza"}}}) 
db.nameCollection.updateMany({_id:5},{$rename:{"address.cityBD":"address.city"}}}) 


// change array
db.nameCollection.updateMany({_id:5},{$set:courses:"js"}})  // it will replace array with "js"
db.nameCollection.updateMany({_id:5},{$set:"courses.0":"js"}}) //it will replace array[0] with "js"

// anonemase
db.nameCollection.updateMany({_id:5,courses:"mvs"},{$set:"courses.$":"js"}}) // $ => it refer select course

// push new element
db.nameCollection.updateMany({_id:5},{$push:{courses:"js"}}) //it will push item in array

// addtoset => add uniqe value
db.nameCollection.updateMany({_id:5},{$addtoset:{courses:"js"}}) //it will push uniqe item in array

// pull remove all items
db.nameCollection.updateone({_id:5},{$pull:{courses:"js"}}) // remove all item "js" in array

// pop remove one item
db.nameCollection.updateone({_id:5},{$pop:{courses:1}}) // remove one item "js" in array 1=>from start array , -1=> from end array



// delete

db.nameCollection.deleteone({condition})
db.nameCollection.deleteone({}) // it will delete one document
db.nameCollection.deleteMany({}) // it will delete all document


*/
