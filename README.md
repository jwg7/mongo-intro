# Mongo Intro

## Insert sample blogs (only one is included in the README per James)

#### Discuss converting datatypes in MongoDB.

db.blogs.insertMany([
	{
	 "createdAt": "2022-04-16T06:33:29.080Z",
	 "title": "fugiat",
	 "text": "Voluptates dicta ut dolorem dolor. Tempora animi facilis dignissimos nostrum tempora soluta asperiores. Aut velit aspernatur rerum doloribus. Voluptate non voluptate consequatur. Et qui recusandae aliquid autem consequatur necessitatibus dolore aut.\nSimilique tempora iure magni. Ut eos eveniet amet officiis ab dicta explicabo est eos. Aperiam sunt ullam ipsam iste. Quam dolorum omnis minus sapiente. Est perferendis aut at non aut est ducimus asperiores porro. Rerum et vero perspiciatis ea facere omnis dolor dolores qui.\nNon voluptates aliquam et praesentium vero adipisci odio. Atque et molestias. Accusamus optio suscipit consequatur necessitatibus possimus ut nostrum et pariatur. Aut nam repellendus ut voluptate molestias et sint. Excepturi et ullam dolor ipsa nulla sapiente et. Suscipit quo consequatur voluptatem qui neque voluptatem voluptate ex.",
	 "author": "Ronald Barrows",
	 "lastModified": "2022-09-17T09:00:54.997Z",
	 "categories": ["nulla", "quasi", "beatae"],
	 "id": "dcc2102d-a20a-4765-8dc4-9079af4fdc9b",
	 "objectId": 1
	}])


## Insert a new blog into the collection

db.blogs.insert([
       {
"createdAt": new Date(),   
"title": 'This is a new blog',
"text": 'This is text for the new blog',
"author": `William Shakespeare's better half`,
"lastModified": new Date(),
"categories": ['blog'],
"id": 'jwg007',
"objectId": 11 
       }
       ])


##  Find one blog by author

db.blogs.find({
    author: 'Alfred Davis'
})
   .projection({})
   .sort({_id:-1})
   .limit(100)

## Find all blogs whose objectId is greater than 5.

db.blogs.find({
    objectId: { $gt: 5 }
})
   .projection({})
   .sort({_id:-1})
   .limit(100)

## Find all blogs whose createdAt is after April 1, 2022

#### Discuss changing data types on this one as well.

db.blogs.find({
    createdAt: {$gt: 2022-04-01}
})
   .projection({})
   .sort({_id:-1})
   .limit(100)

## Find all blogs where the field lastModified exists

#### Discuss. Only 8 out of 10 showed up in Mongo. All ten had the lastModified field.

db.blogs.find({
    lastModified: {
        $exists: true
    }
})

 ## Find all blogs where the createdAt type is a date

db.blogs.find({ "createdAt": {$type: "date"} })