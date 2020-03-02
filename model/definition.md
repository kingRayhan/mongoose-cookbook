## Defining schema

```js
var mongoose = require("mongoose")
var Schema = mongoose.Schema

var blogSchema = new Schema({
  title: String, // String is shorthand for {type: String}
  author: String,
  body: String,
  comments: [{ body: String, date: Date }],
  date: { type: Date, default: Date.now },
  hidden: Boolean,
  meta: {
    votes: Number,
    favs: Number
  }
})
```

#### Types

- `String`
- `Boolean`
- `Number`
- `Date`
- `Array`
- `Buffer`
- `Schema.Types.Mixed`
- `Schema.Types.ObjectId`

#### Difine a model

```js
  const MODEL = mongoose.model(MODEL_NAME', MODEL_SCHEMA);
```
