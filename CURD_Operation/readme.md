# MongoDB CRUD Operations

## Introduction
This guide covers CRUD (Create, Read, Update, Delete) operations in MongoDB using the **MongoDB shell** and **MongoDB Compass**.

## Prerequisites
- Install [MongoDB](https://www.mongodb.com/try/download/community)
- Start MongoDB server

## Connect to MongoDB
Open the terminal and run:
```sh
mongosh
```
This opens the MongoDB shell.

## Create a Database
To create and switch to a new database:
```sh
use mydatabase
```
If the database doesn’t exist, MongoDB will create it when you insert data.

## Create a Collection
```sh
db.createCollection("users")
```
Alternatively, collections are created automatically when inserting documents.

## CRUD Operations

### 1. Create (Insert) Documents
#### Insert One Document:
```sh
db.users.insertOne({ name: "Alice", email: "alice@example.com", age: 25, city: "New York" })
```
#### Insert Multiple Documents:
```sh
db.users.insertMany([
    { name: "Bob", email: "bob@example.com", age: 30, city: "Los Angeles" },
    { name: "Charlie", email: "charlie@example.com", age: 28, city: "Chicago" },
    { name: "David", email: "david@example.com", age: 35, city: "San Francisco" }
])
```

### 2. Read (Find) Documents
#### Find All Documents:
```sh
db.users.find()
```
#### Find One Document:
```sh
db.users.findOne({ name: "Alice" })
```
#### Find Documents with a Condition:
```sh
db.users.find({ age: { $gt: 25 } })
```
#### Find Documents with Multiple Conditions (AND):
```sh
db.users.find({ age: { $gt: 25 }, city: "Los Angeles" })
```
#### Find Documents with OR Condition:
```sh
db.users.find({ $or: [{ age: { $lt: 30 } }, { city: "Chicago" }] })
```
#### Find Specific Fields (Projection):
```sh
db.users.find({}, { name: 1, email: 1, _id: 0 })
```

### 3. Update Documents
#### Update One Document:
```sh
db.users.updateOne(
    { name: "Alice" },
    { $set: { age: 26, city: "Boston" } }
)
```
#### Update Multiple Documents:
```sh
db.users.updateMany(
    { age: { $lt: 30 } },
    { $set: { status: "active" } }
)
```
#### Increment a Field Value:
```sh
db.users.updateOne(
    { name: "Bob" },
    { $inc: { age: 1 } }
)
```
#### Rename a Field:
```sh
db.users.updateMany(
    {},
    { $rename: { "city": "location" } }
)
```

### 4. Delete Documents
#### Delete One Document:
```sh
db.users.deleteOne({ name: "Bob" })
```
#### Delete Multiple Documents:
```sh
db.users.deleteMany({ age: { $gt: 30 } })
```
#### Delete All Documents:
```sh
db.users.deleteMany({})
```

## Additional Operations

### Sorting Data
#### Sort Users by Age (Ascending):
```sh
db.users.find().sort({ age: 1 })
```
#### Sort Users by Age (Descending):
```sh
db.users.find().sort({ age: -1 })
```

### Limit and Skip
#### Limit Results to 2 Users:
```sh
db.users.find().limit(2)
```
#### Skip First 2 Users and Show Next 2:
```sh
db.users.find().skip(2).limit(2)
```

### Counting Documents
```sh
db.users.countDocuments()
```
```sh
db.users.countDocuments({ city: "Chicago" })
```

### Show Databases and Collections
#### List All Databases:
```sh
show dbs
```
#### List Collections in the Current Database:
```sh
show collections
```

## Drop Database and Collection
#### Delete a Collection:
```sh
db.users.drop()
```
#### Delete a Database:
```sh
db.dropDatabase()
```


