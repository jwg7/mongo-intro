# Mongo Intro

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
"objectId": '11'  
       }
       ])


##  Find one blog by author
db.blogs.find({
    author: 'Alfred Davis'
})
   .projection({})
   .sort({_id:-1})
   .limit(100)

## Find all blogs whose objectId is greater than 5

### Of note: The data provided had the objectId as a string, not a number. This was able to be completed by searching for a string.


db.blogs.find({
    objectId: { $gt: '5' }
})
   .projection({})
   .sort({_id:-1})
   .limit(100)

## Find all blogs whose createdAt is after April 1, 2022

db.blogs.find({
    createdAt: {$gt: 2022-04-01}
})
   .projection({})
   .sort({_id:-1})
   .limit(100)

