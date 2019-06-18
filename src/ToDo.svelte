<script>
  let todo;
  let { title, taskList, id, urgent } = todo;
</script>

<style></style>

<article class="todo-card">
  <h3>{title}</h3>
  <ul>
    {#each taskList as task (task.id)}
      <li>{task.title}</li>
    {/each}
  </ul>
</article>