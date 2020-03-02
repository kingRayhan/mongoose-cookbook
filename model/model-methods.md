#### Mongoose Model Methods

- `find(criteria, [fields], [options], [callback])`: find document; callback has error and documents arguments
- `count(criteria, [callback]))`: return a count; callback has error and count arguments
- `findById(id, [fields], [options], [callback])`: return a single document by ID; callback has error and document arguments
- `findByIdAndUpdate(id, [update], [options], [callback])`: executes MongoDB's findAndModify to update by ID
- `findByIdAndRemove(id, [options], [callback])`: executes MongoDB's findAndModify to remove
- `findOne(criteria, [fields], [options], [callback])`: return a single document; callback has error and document arguments
- `findOneAndUpdate([criteria], [update], [options], [callback])`: executes MongoDB's findAndModify to update
- `findOneAndRemove(id, [update], [options], [callback])`: executes MongoDB's findAndModify to remove
- `update(criteria, update, [options], [callback])`: update documents; callback has error, and count arguments
- `create(doc(s), [callback])`: create document object and save it to database; callback has error and doc(s) arguments
- `remove(criteria, [callback])`: remove documents; callback has error argument

#### Mongoose Document Methods

- `save([callback])`: save the document; callback has error, doc and count arguments
- `set(path, val, [type], [options])`: set value on the doc's property
- `get(path, [type])`: get the value
- `isModified([path])`: check if the property has been modified
- `populate([path], [callback])`: populate reference
- `toJSON(options)`: get JSON from document
- `validate(callback)`: validate the document

#### Query Helpers

```js
animalSchema.query.byName = function(name) {
  return this.where({ name: new RegExp(name, "i") })
}

var Animal = mongoose.model("Animal", animalSchema)

Animal.find()
  .byName("fido")
  .exec(function(err, animals) {
    console.log(animals)
  })

Animal.findOne()
  .byName("fido")
  .exec(function(err, animal) {
    console.log(animal)
  })
```
