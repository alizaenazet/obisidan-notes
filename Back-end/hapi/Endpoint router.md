 ```js
const router = [

			{
method:"GET", //Menthod operasi pada Endpoint
path:"/notes/{userId}", //Path url route
handler: ()=>{return "its handler"} // fungsi bekerja saat endpoint dipanggil
			}
]
```

```jsx
const {getAllNotes} = require('../handler/notest-todo');

const router = [

	{
	method:"GET",
	path:"/notes/{userId}",
	handler: getAllNotes // fungsi di import pada file terpisah
	}

]  

module.exports = router
```

