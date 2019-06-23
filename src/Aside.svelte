<script>
  import { onMount, createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let titleInput = '';
  let taskInput = '';
  let taskList = [];
  let makeTaskButton;
  let titleInputElement;
  let taskInputElement;
  let clearAllButton;

  onMount(() => {
    titleInputElement.focus();
    makeTaskButton.setAttribute('disabled', true);
    clearAllButton.setAttribute('disabled', true);
  });

  const handleChange = () => {
    if (titleInput && (taskInput || taskList.length)) {
      makeTaskButton.removeAttribute('disabled');
      clearAllButton.removeAttribute('disabled');
    } else {
      makeTaskButton.setAttribute('disabled', true);
      clearAllButton.setAttribute('disabled', true);
    }
  }

  const addTask = () => {
    const element = taskInputElement
    if (element.value) {
      taskList = [...taskList, {title: element.value, id: Date.now()}]
      taskInput = '';
      element.focus();
    }

    handleChange();
  }

  const removeTask = (e) => {
    e.target.closest('li').remove();
  }

  const makeToDo = () => {
    dispatch('addToDo', {
      title: titleInput,
      tasks: taskList,
      id: Date.now(),
      urgent: false
    });

    clearForm();
  }

  const clearForm = () => {
    titleInput = '';
    taskInput = '';
    taskList = [];
    titleInputElement.focus();
    handleChange();
  }

</script>

<style>
  aside {
    background: #587A8A;
    grid-area: aside;
    padding: 10px;
    color: lightgray;
  }

  ul {
    list-style: none;
  }

</style>

<aside>
  <form on:keyup={handleChange}>
    <label for="title-input">ToDo Title</label>
    <input type="text" id="title-input" bind:value={titleInput} bind:this={titleInputElement}>
    <section id="task-area">
      <ul id="aside-task-list">
        {#each taskList as task (task.id)}
          <li>
            {task.title}
            <button class="remove-task-item-button" on:click|preventDefault={removeTask}>X</button>
          </li>
        {/each}
      </ul>
    </section>
    <label for="task-input">Task Item</label>
    <input type="text" id="task-input" bind:value={taskInput} bind:this={taskInputElement}>
    <button on:click|preventDefault={addTask}>+</button>
    <button id="make-task-button" on:click|preventDefault={makeToDo} bind:this={makeTaskButton}>Make Task List</button>
    <button id="clear-all-button" on:click|preventDefault={clearForm} bind:this={clearAllButton}>Clear All</button>
    <hr>
    <button>Filter By Urgency</button>
  </form>
</aside>
