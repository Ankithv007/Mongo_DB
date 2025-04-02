# MongoDB Data Types

MongoDB supports a variety of data types to store and manipulate data efficiently. Below are the primary data types used in MongoDB:

## 1. String
- Used to store text.
- Example:
  ```json
  { "name": "John Doe" }
  ```

## 2. Integer
- Used to store numerical values (both 32-bit and 64-bit integers).
- Example:
  ```json
  { "age": 30 }
  ```

## 3. Double
- Used to store floating-point numbers.
- Example:
  ```json
  { "price": 99.99 }
  ```

## 4. Boolean
- Used to store `true` or `false` values.
- Example:
  ```json
  { "isActive": true }
  ```

## 5. Array
- Used to store multiple values in a single field.
- Example:
  ```json
  { "hobbies": ["reading", "gaming", "coding"] }
  ```

## 6. Object (Embedded Document)
- Used to store nested documents.
- Example:
  ```json
  { "address": { "city": "New York", "zip": "10001" } }
  ```

## 7. ObjectId
- A unique identifier assigned to each document.
- Example:
  ```json
  { "_id": ObjectId("507f1f77bcf86cd799439011") }
  ```

## 8. Date
- Used to store date and time values.
- Example:
  ```json
  { "createdAt": ISODate("2023-03-30T12:00:00Z") }
  ```

## 9. Null
- Represents a `null` value.
- Example:
  ```json
  { "deletedAt": null }
  ```

## 10. Binary Data
- Used to store binary data like images or files.
- Example:
  ```json
  { "file": BinData(0, "base64encodeddata") }
  ```

## 11. Regular Expression
- Used for pattern matching in queries.
- Example:
  ```json
  { "name": { "$regex": "^J" } }
  ```

## 12. JavaScript Code
- Stores JavaScript code that can be executed within MongoDB.
- Example:
  ```json
  { "script": Code("function() { return true; }") }
  ```

## 13. Decimal128
- Used to store high-precision decimal values.
- Example:
  ```json
  { "amount": NumberDecimal("12345.6789") }
  ```

## 14. Timestamp
- Used to store timestamp values for versioning and replication.
- Example:
  ```json
  { "timestamp": Timestamp(1629384938, 1) }
  ```

## 15. Min/Max Keys
- Used to compare values against the lowest (`MinKey`) and highest (`MaxKey`) BSON elements.
- Example:
  ```json
  { "minValue": MinKey(), "maxValue": MaxKey() }
  ```

---

## Example Collection Using These Data Types

To better understand these data types, here is an example MongoDB collection named `users` with documents utilizing various data types:

```json
{
  "_id": ObjectId("507f1f77bcf86cd799439011"),
  "name": "John Doe",
  "age": 30,
  "price": 99.99,
  "isActive": true,
  "hobbies": ["reading", "gaming", "coding"],
  "address": { "city": "New York", "zip": "10001" },
  "createdAt": ISODate("2023-03-30T12:00:00Z"),
  "deletedAt": null,
  "file": BinData(0, "base64encodeddata"),
  "namePattern": { "$regex": "^J" },
  "script": Code("function() { return true; }"),
  "amount": NumberDecimal("12345.6789"),
  "timestamp": Timestamp(1629384938, 1),
  "minValue": MinKey(),
  "maxValue": MaxKey()
}
```

This document provides a practical example of how different MongoDB data types can be used within a collection.

---

### Conclusion
Understanding these data types is crucial for efficient MongoDB schema design and querying. Choose the appropriate data type based on your application needs to optimize performance and storage.