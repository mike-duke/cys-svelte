<script>
  import Aside from './Aside.svelte';
  import ToDo from './ToDo.svelte';
  import Header from './Header.svelte';
  let todos = [];

  const addToDo = (todo) => {
    todos = [todo.detail, ...todos];
  }

</script>

<style>
  #todo-list {
    grid-area: main;
    display: flex;
    flex-wrap: wrap;
    overflow: scroll;
    background: #F3F6F7;
  }

  #instruction-card {
    height: 400px;
    width: 300px;
    border: 8px dashed gray;
    color: gray;
    margin: 20px;
    padding: 20px;
  }
</style>

<Header />
<Aside on:addToDo={addToDo} />
<section id="todo-list">
  {#if todos.length < 1}
    <article id="instruction-card">
      <h2>Create a ToDo with a task list using the form on the left side of the page</h2>
    </article>
  {:else}
    {#each todos as todo (todo.id)}
      <ToDo todo={todo} />
    {/each}
  {/if}
</section>