### Connection and installation

```bash
npm install mongoose
// or
yarn add mongoose
```

#### Connection

```js
mongoose
  .connect( < DATABASE_COLLECTION_STRING > , {
    useNewUrlParser: true,
    useUnifiedTopology: true
  })
  .then(() => console.log("Database connected"))
  .catch(e => console.log("Error connecting db", e.message))
```

#### Connection events

Listen for error events on the connection.

```js
mongoose.connection.on(<EVENT_TYPE>, msg => {
  // msg
})
```

** Connection Events **

- `connecting`: Emitted when Mongoose starts making its initial connection to the MongoDB server
- `connected`: Emitted when Mongoose successfully makes its initial connection to the MongoDB server
- `open`: Equivalent to `connected`
- `disconnecting`: Your app called [`Connection#close()`](https://mongoosejs.com/docs/api.html#connection_Connection-close) to disconnect from MongoDB
- `disconnected`: Emitted when Mongoose lost connection to the MongoDB server. This event may be due to your code explicitly closing the connection, the database server crashing, or network connectivity issues.
- `close`: Emitted after [`Connection#close()`](https://mongoosejs.com/docs/api.html#connection_Connection-close) successfully closes the connection. If you call `conn.close()`, you'll get both a 'disconnected' event and a 'close' event.
- `reconnected`: Emitted if Mongoose lost connectivity to MongoDB and successfully reconnected. Mongoose attempts to [automatically reconnect](https://thecodebarbarian.com/managing-connections-with-the-mongodb-node-driver.html) when it loses connection to the database.
- `error`: Emitted if an error occurs on a connection, like a `parseError` due to malformed data or a payload larger than [16MB](https://docs.mongodb.com/manual/reference/limits/#BSON-Document-Size).
- `fullsetup`: Emitted when you're connecting to a replica set and Mongoose has successfully connected to the primary and at least one secondary.
- `all`: Emitted when you're connecting to a replica set and Mongoose has successfully connected to all servers specified in your connection string.
- `reconnectFailed`: Emitted when you're connected to a standalone server and Mongoose has run out of [`reconnectTries`](https://thecodebarbarian.com/managing-connections-with-the-mongodb-node-driver.html#handling-single-server-outages). The [MongoDB driver](http://npmjs.com/package/mongodb) will no longer attempt to reconnect after this event is emitted. This event will never be emitted if you're connected to a replica set.
