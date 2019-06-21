<script>
  import Aside from './Aside.svelte';
  import ToDo from './ToDo.svelte';
  import Header from './Header.svelte';
  let todos = []

  const addToDo = (todo) => {
    todos = [...todos, todo.detail];
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
</style>

<Header />
<Aside on:addToDo={addToDo} />
<section id="todo-list">
  {#each todos as todo (todo.id)}
    <ToDo todo={todo} />
  {/each}
</section>