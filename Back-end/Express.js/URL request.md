**

-   **req.originalUrl** :  mendapat url secara full beserta query param nya
    
-   **req.path** :  mendapatkan path url tanpa query param
    
-   **req.hostname** :  mendapatkan nama host atau domain dari web kita
    
-   **req.protocol** : mendapatkan protocol dari url web
    
-   **req.secure** : mengecek apakah url web nya https atau bukan
    
-   **req.subdomains** :  mendapatkan array subdomain dari url web kita
    

**

```js
app.get('/hello/world', (req,res) =>{

res.json({
path: req.path,
originalUrl: req.originalUrl,
hostName: req.hostname,
protocol : req.protocol
})

})
```

