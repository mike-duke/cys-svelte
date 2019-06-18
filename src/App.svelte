<script>
  import Aside from './Aside.svelte';
  import ToDo from './ToDo.svelte';
  let todos = []
</script>

<style></style>

<Aside/>
<section id="todo-list">
  {#each todos as todo (todo.id)}
    <ToDo todo/>
  {/each}
</section>