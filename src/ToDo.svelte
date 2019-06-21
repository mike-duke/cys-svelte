<script>
  export let todo;
  let { title, tasks, id, urgent } = todo;
</script>

<style>
  .todo-card {
    height: 400px;
    width: 300px;
    margin: 20px;
    padding: 10px;
  }

  .todo-card:nth-child(even) {
    background: #FAFDFF;
    border: 2px solid #C7D3D8;
  }

  .todo-card:nth-child(odd) {
    background: #FFE89D;
    border: 2px solid #FFC30C;
  }

  hr {
    color: gray;
  }
</style>

<article class="todo-card">
  <h3>{title}</h3>
  <hr>
  <ul>
    {#each tasks as task (id)}
      <li>{task.title}</li>
    {/each}
  </ul>
  <hr>
  <button>Urgent</button>
  <button>Delete</button>
</article>