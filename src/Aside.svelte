<script>
  import { onMount, createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let titleInput = '';
  let taskInput = '';
  let taskList = [];

  onMount(() => {
    document.querySelector('#title-input').focus();    
  })

  const addTask = () => {
    let element = document.querySelector('#task-input');
    taskList = [...taskList, {title: element.value, id: Date.now()}]
    taskInput = '';
    element.focus();
  }

  const makeToDo = () => {
    console.log('hello');
    dispatch('addToDo', {
      title: titleInput,
      tasks: taskList,
      id: Date.now(),
      urgent: false
    });

    titleInput = '';
    taskInput = '';
    taskList = [];
  }
</script>

<style>

</style>

<aside>
  <form action="">
    <label for="title-input">ToDo Title</label>
    <input type="text" id="title-input" bind:value={titleInput}>
    <section id="task-area">
      <ul id="aside-task-list">
        {#each taskList as task (task.id)}
          <li>{task.title}</li>
        {/each}
      </ul>
    </section>
    <label for="task-input">Task Item</label>
    <input type="text" id="task-input" bind:value={taskInput}>
    <button on:click|preventDefault={addTask}>+</button>
    <button id="make-task-button" on:click|preventDefault={makeToDo}>Make Task List</button>
    <button>Clear All</button>
    <hr>
    <button>Filter By Urgency</button>
  </form>
</aside>
