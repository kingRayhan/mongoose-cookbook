```js
// Create
var post = new Post({title: 'a', text: 'b')
post.save(function(error, document){
  ...
})


// Read
Post.findOne(criteria, function(error, post) {
  ...
})

// Update
Post.findOne(criteria, function(error, post) {
  post.set()
  post.save(function(error, document){
    ...
  })
})

// Delete
Post.findOne(criteria, function(error, post) {
  post.remove(function(error){
    ...
  })
})
```
