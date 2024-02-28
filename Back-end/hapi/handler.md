
```jsx
async function getAllNotes(req,h) {

const userId = req.params.userId;
const notes = await getNotes(userId);

if (!notes) {  // pengecekan pada data
const response = h.response({ //response yang diberikan
status: "not found",
})

response.code(204) // response code 
return response; // melakukan return response untuk digunakan pada route handler
}

const response = h.response({
status: "succes",
data:{
notes
}

})
response.code(200)
return response

}
```



```jsx
const {getNotes} = require('../controller/notes-todo'); //controller pada logic bisnis

async function getAllNotes(req,h) {
const userId = req.params.userId;
const notes = await getNotes(userId);

if (!notes) {
const response = h.response({
status: "not found",
})

response.code(204)
return response;
}

const response = h.response({
status: "succes",
data:{
notes
}

})

response.code(200)

return response
}


module.exports = {getAllNotes}
```