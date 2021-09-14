# MongoDb

## What is MongoDb??

it's Document-based DataBase (No-SQL DataBase)

MongoDB is a document database with the scalability and flexibility that you want with the querying and indexing that you need

> ### Features Of MongoDB:

- **Document Based**: MongoDB store data in a document(field-value pair data structures, NoSQL).

- **Scalable**:Very easy to distribute data across multiple machines as your users and amount of data grows.

- **Flexible**:No document data schema required, so each document can have different number and type of fields.

- **Performance**: Embedded data models, indexing, sharding, flexible documents, native duplication, etc.

- **Free and open source**,published under the SSPL License.

### some commands and what they do:

- you can run the MongoDB on shell with:

```shell
mongo
```

- Show All Databases
  :

```shell
moshow dbsngo
```

- Show Current Database
  :

```shell
db
```

- Switch Database and if not exist will Create new one:

```shell
use db_name
```

- Drop:

```shell
db.dropDatabase()
```

- Create Collection
  :

```shell
db.createCollection('collection_name')
```

- Show Collections:

```shell
show collections
```

- Get All Rows:

```shell
db.collection_name.find()
```

- Get All Rows Formatted:

```shell
db.collection_name.find().pretty()
```

- Find Rows:

```shell
db.collection_name.find({ difficulty: 'easy' })

```

- Find Rows with one criteria(price) that have number less than 500:

```shell
db.collection_name.find({ price: {$lt: 500} })

```

- Find Rows with tow criteria(price and rating), price that have number less or equal than 500 and rating that have number Greater or equal than 4.8:

```shell
db.collection_name.find({ price: {$lte: 500}, rating:{$gte:4.8}  })

```

- Find Rows with tow criteria(price or rating), price that have number less or equal than 500 and rating that have number Greater or equal than 4.8:

```shell
db.collection_name.find({ $or:[{price: {$lte: 500}}, {rating:{$gte:4.8}}]  })

```

- Find Rows with tow criteria(price or rating), price that have number less or equal than 500 and rating that have number Greater or equal than 4.8 and just select one field witch is Name :

```shell
db.collection_name.find({ $or:[{price: {$lte: 500}}, {rating:{$gte:4.8}}],{name:1} })

```

- Sort Rows:

```shell
# asc
db.collection_name.find().sort({ title: 1 }).pretty()
# desc
db.collection_name.find().sort({ title: -1 }).pretty()
```

- Count Rows:

```shell
db.collection_name.find().count()
db.collection_name.find({ category: 'news' }).count()
```

- Limit Rows

```shell
db.collection_name.find().limit(2).pretty()
```

- Chaining

```shell
db.collection_name.find().limit(2).sort({ title: 1 }).pretty()
```

- Foreach

```shell
db.collection_name.find().forEach(function(doc) {
  print("Blog Post: " + doc.title)
})
```

- Find One Row

```shell
db.collection_name.findOne({ category: 'News' })
```

- Find Specific Fields

```shell
db.collection_name.find({ title: 'Post One' }, {
  title: 1,
  author: 1
})
```

- Update Row

> Note: we have UpdateOne and UpdateMany methods

```shell
db.collection_name.update({ title: 'Post Two' },
{
  title: 'Post Two',
  body: 'New body for post 2',
  date: Date()
},
{
  upsert: true
})
```

- Update Specific Field

```shell
db.collection_name.update({ title: 'Post Two' },
{
  $set: {
    body: 'Body for post 2',
    category: 'Technology'
  }
})
```

- Increment Field (\$inc)

```shell
db.collection_name.update({ title: 'Post Two' },
{
  $inc: {
    likes: 5
  }
})
```

- Rename Field

```shell
db.collection_name.update({ title: 'Post Two' },
{
  $rename: {
    likes: 'views'
  }
})
```

- Delete Row

> Note: we have UpdateOne and UpdateMany methods

> **Warning**: if you use empty obj "{}" inside DeleteMany method it will remove all documents.

```shell
db.collection_name.remove({ title: 'Post Four' })
```

- Sub-Documents

```shell
db.collection_name.update({ title: 'Post One' },
{
  $set: {
    comments: [
      {
        body: 'Comment One',
        user: 'Mary Williams',
        date: Date()
      },
      {
        body: 'Comment Two',
        user: 'Harry White',
        date: Date()
      }
    ]
  }
})
```

- Find By Element in Array (\$elemMatch)

```shell
db.collection_name.find({
  comments: {
     $elemMatch: {
       user: 'Mary Williams'
       }
    }
  }
)
```

- Add Index

```shell
db.collection_name.createIndex({ title: 'text' })
```

- Text Search

```shell
db.collection_name.find({
  $text: {
    $search: "\"Post O\""
    }
})
```

- Greater & Less Than

```shell
db.collection_name.find({ views: { $gt: 2 } })
db.collection_name.find({ views: { $gte: 7 } })
db.collection_name.find({ views: { $lt: 7 } })
db.collection_name.find({ views: { $lte: 7 } })
```

---

[Credit Source](https://gist.github.com/bradtraversy/f407d642bdc3b31681bc7e56d95485b6)

[Home](../README.md)
