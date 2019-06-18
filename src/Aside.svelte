<script>
  let titleInput = '';
  let taskInput = '';
</script>

<aside>
  <form action="">
    <label for="title-input">ToDo Title</label>
    <input type="text" id="title-input" value={titleInput}>
    <section id="task-area"></section>
    <label for="task-input">Task Item</label>
    <input type="text" id="task-input" value={taskInput}>
    <button>+</button>
    <button>Make Task List</button>
    <button>Clear All</button>
    <hr>
    <button>Filter By Urgency</button>
  </form>
</aside>

<style>

</style>