#####获取启动端口

```ts
const server = app.listen(PORT);
console.log(server.address().port);
```

#####获取get参数

```ts
console.log('query: ', ctx.query);
console.log('querystring: ', ctx.querystring);
```

#####获取post参数

```ts
// 需要解析body中间件
import bodyParse from 'koa-bodyparser';
app.use(bodyParse());

console.log('request: ', ctx.request.body);
```