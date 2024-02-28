amethod yang terdapat pada request :
https://expressjs.com/en/4x/api.html#req

contoh :

```js
const app = express();

app.get('/', (req,res) =>{
res.send(`hello ${req.query.name}`)
}) 
```
*mengambil nama pada query*

