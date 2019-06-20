<script>
  export let todo;
  let { title, tasks, id, urgent } = todo;
</script>

<style></style>

<article class="todo-card">
  <h3>{title}</h3>
  <ul>
    {#each tasks as task (id)}
      <li>{task.title}</li>
    {/each}
  </ul>
  <button>Urgent</button>
  <button>Delete</button>
</article>