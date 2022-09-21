# Mongo Intro

## Insert sample blogs (only one is included in the README per James)

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

## Find one blog by author

db.blogs.find({
author: 'Alfred Davis'
})

## Find all blogs whose objectId is greater than 5.

db.blogs.find({
objectId: { $gt: 5 }
})

## Find all blogs whose createdAt is after April 1, 2022

db.blogs.find({
createdAt: { $gt: new Date("2022-04-01") }

})

## Find all blogs where the field lastModified exists

db.blogs.find({
lastModified: {
$exists: true
}
})

## Find all blogs where the createdAt type is a date

db.blogs.find({ createdAt: {$type: "date"} })

## Find all blogs in which the lastModified does not exist and set it

db.blogs.updateMany({ lastModified: { $exists: false } },{ $set:{ lastModified: new Date() }});

From now on, all the following queries should update lastModified to be the current datetime

## Find all blogs created after May 2022 and add "lorem" as a new category in the categories array

db.blogs.updateMany({ createdAt:{ $gt: new Date("2022-05") } },{ $set:{ lastModified: new Date() }, $push: { categories: "lorem" } });

## Find all blogs that have the category "voluptas" and pull "voluptas" from the categories

db.blogs.updateMany({ categories:{ $in: ["voluptas"] } },{ $set:{ lastModified: new Date() }, $pull: { categories: "voluptas" } });

## Find all blogs with "corrupti" in the categories and delete those blogs

db.blogs.deleteMany({ categories: "corrupti" });
