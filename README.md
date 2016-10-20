# js-api
Creates a REST API server from given JavaScript/JSON objects. Uses [Koa](https://github.com/koajs/koa) for the REST API.

## Example
```javascript
var jsapi = require('js-api'); // this is a regular Koa app
var data = {posts: [{id: 1, title: 'first post', body: 'lorem ip sum'}], users: [{id: 1, name: 'Chuck'}]};

// define custom API route for 'users'
data.users.route = '/local-users'

// define custom Koa middleware/routes if necessary
jsapi.use(function *(next){
  var start = new Date;
  yield next;
  var ms = new Date - start;
  console.log('%s %s - %s', this.method, this.url, ms);
});

jsapi.start(data, 3000);
```

## License
MIT
