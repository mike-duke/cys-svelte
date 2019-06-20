<script>
  import Aside from './Aside.svelte';
  import ToDo from './ToDo.svelte';
  import Header from './Header.svelte';
  let todos = []

  const addToDo = (todo) => {
    todos = [...todos, todo.detail]
    console.log(todos)
  }

</script>

<style>
  #todo-list {
    grid-area: main;
  }
</style>

<Header />
<Aside on:addToDo={addToDo} />
<section id="todo-list">
  {#each todos as todo (todo.id)}
    <ToDo todo={todo} />
  {/each}
</section>