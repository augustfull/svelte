---
title: Each block bindings
---

You can even bind to properties inside an `each` block.

```html
{#each todos as todo}
	<input
		type=checkbox
		bind:checked={todo.done}
	>

	<input
		placeholder="What needs to be done?"
		bind:value={todo.text}
	>
{/each}
```

> Note that interacting with these `<input>` elements will mutate the array. If you prefer to work with immutable data, you should avoid these bindings and use event handlers instead. But if you find working with each block bindings helpful, you can always create another variable and copy the data of your array to the new variable and use the new variable in each block. This way the data in the array remains immutable.

```html
let todos = [
		{done: false, text: "some important text"},
		{done: false, text: "another important text"},
		{done: false, text: "some regular text"}
];

let mut_todos = [...todos];  // mut means mutable

{#each mut_todos as todo}
	<input
		type=checkbox
		bind:checked={todo.done}
	>

	<input
		placeholder="What needs to be done?"
		bind:value={todo.text}
	>
{/each}
```
