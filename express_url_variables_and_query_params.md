> http://stackoverflow.com/questions/20089582/how-to-get-url-parameter-in-express-node-js

> To get a URL parameter's value, use req.params

---

```
app.get('/p/:tagId', function(req, res) {
  res.send("tagId is set to " + req.params.tagId);
});

// GET /p/5
// tagId is set to 5
```

---

> If you want to get a query parameter ?tagId=5, then use req.query

```
app.get('/p', function(req, res) {
  res.send("tagId is set to " + req.query.tagId);
});

// GET /p?tagId=5
```