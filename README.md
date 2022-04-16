# mongolite
Lite mongodb engine in python

## Support
The goal of this project is to create sqlite version for mongodb

For now the library is supporting:
- insert_many / insert_one
- update_many / update_one
    - $set
    - $inc
    - $addToSet
- find / find_one
    - field matching
    - filter fields
- replace_many / replace_one
- create_collection
- get_collection
- drop_collection
- create_database
- drop_database
- thread safety
- replaceable storage engine

## Examples
```python
from mongolite import MongoClient

with MongoClient(dirpath="~/my_db_dir", database="my_db") as client:
    db = client.get_default_database()
    collection = db.get_collection("users")

    collection.insert_one({"name": "yoyo"})
    collection.update_one({"name": "yoyo"}, {"$set": {"age": 20}})
    user = collection.find_one({"age": 20})
    print(user) # -> {"name": "yoyo", "age": 20}
```

```python
from mongolite import MongoClient

client = MongoClient(dirpath="~/my_db_dir", database="my_db")

db = client.get_default_database()
collection = db.get_collection("users")

collection.insert_one({"name": "yoyo"})
collection.update_one({"name": "yoyo"}, {"$set": {"age": 20}})
user = collection.find_one({"age": 20})
print(user) # -> {"name": "yoyo", "age": 20}

client.close()
```

#### Note for developers using