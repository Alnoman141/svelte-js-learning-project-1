<script>
  import { tasks } from '../src/store';
  export let showTaskForm = false;
  export let showTaskList = true;
  export let filter = 'all';

  function changeFilter(filterName){
      filter = filterName;
  }

  function clearTask(){
      let tempTasks = $tasks.filter(t => !t.isCompleted);
      tasks.set(tempTasks);
  }
</script>

<main>
  <div class="row mb-3 text-center">
    <div class="col-md-6 offset-md-3">
      <button
        on:click={() => showTaskForm = !showTaskForm}
        class="btn btn-success btn-sm"
        >Create
      </button>
      <button
        on:click={() => showTaskList = !showTaskList}
        class="btn btn-warning btn-sm">{ showTaskList ? 'Hide' : 'Show'}</button
      >
      <button on:click="{() => changeFilter('all')}" class="btn btn-primary btn-sm">All</button>
      <button on:click="{() => changeFilter('active')}" class="btn btn-secondary btn-sm">Active</button>
      <button on:click="{() => changeFilter('completed')}" class="btn btn-secondary btn-sm">Completed</button>
      <button on:click="{clearTask}" class="btn btn-danger btn-sm">Clear</button>
    </div>
  </div>
</main>
<style>
    .btn {
        margin: 0px 2px;
    }
</style>
