get many inputs value 
```tsx
function TodoList() {

async function handleAddTodo(event: React.SyntheticEvent<HTMLFormElement>) {
event.preventDefault()

const target = event.target as typeof event.target & {
	todoInsert: {value: string},
	}

const insteredTodo = target.todoInsert.value
console.log(insteredTodo);
}

return (

<div>

<form onSubmit={handleAddTodo}>
<h3>Add todo</h3
<input name='todoInsert'></input>
<button type='submit'>Add</button>
</form>

</div>

	)
}

```