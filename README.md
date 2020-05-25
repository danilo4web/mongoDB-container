# MongoDB - Docker Container:

#### To start server:
```
$ docker-compose up -d

$ docker exec -it mongodbcontainer_mongo_1 bash
```

#### Or just:
```
docker run -d -p 27017-27019:27017-27019 --name mongodb mongo:4.0.4
```

#### Mongo terminal:
```
$ mongo
```

### Basic mongoDB commands:
```
$ db.version()
$ show dbs
$ show dbs
$ show collections
$ use newdb

$ db.user.save({name: "Dani", lastname: "Pereira", age: 34})
$ db.user.find({name: "Dani"})

$ db.user.update({name: "Dani"}, {name: "Danilo", lastname: "Pereira", age: 35})
$ db.user.find({name: "Danilo"})

$ db.user.updateOne({name: "Danilo"}, {$set: {age: 36}})
$ db.user.find({name: "Danilo"})

$ db.user.remove({_id:ObjectId("")});
$ db.user.find({name: "Danilo"})

$ db.user.find( {$or: [{name: "Danilo"}, {name:"Maria"}]})
```

### PHP Driver
```
$ composer require mongodb/mongodb
```

### Connect to MongoDB
```
<?php

$manager = new \MongoDB\Driver\Manager(
    'mongodb://mongo:27017'
);
```

### Search Example
```
<?php

$filter = ['name' => 'Danilo'];
$options = [];
$query = new \MongoDB\Driver\Query($filter, $options);
$response = $manager->executeQuery('db.user', $query);
```
