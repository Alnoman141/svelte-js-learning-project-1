<script context="module">
  import CreateTask from "../components/CreateTask.svelte";
  import Tasks from "../components/Tasks.svelte";
  import Buttons from "../components/Buttons.svelte";
  import { tasks } from "./store.js";
  //   import { onDestroy } from 'svelte';
</script>

<script>
  // normal way
  //    let tasks = [];
  //   $: console.log(tasks);
  //   function newTaskCreated(e) {
  //     console.log(e);
  //     tasks = [e.detail, ...tasks];
  //   }

  //   store management way

  // details way
  // const unsubscribe = tasks.subscribe((value) => {
  //     tasks = value;
  // });

  // onDestroy(() => {
  //     unsubscribe();
  // })
  // short way
  $: console.log($tasks);
  let toggleTasKForm = false;
  let toggleTaskList = true;
  let filter = "all";

  $: activeTask = $tasks.filter((t) => !t.isCompleted);
  $: completeTask = $tasks.filter((t) => t.isCompleted);
</script>

<main class="container my-5">
  <h1 class="display-4 my-3">My First Svelte App</h1>
  <!-- <CreateTask on:taskCreated={newTaskCreated} /> -->

  <Buttons
    bind:showTaskForm={toggleTasKForm}
    bind:showTaskList={toggleTaskList}
    bind:filter
  />

  {#if toggleTasKForm}
    <CreateTask />
  {/if}
  {#if toggleTaskList}
    <div class="row">
      <div class="col-md-6 offset-md-3">
        <div class="card card-body">
          {#if filter === "all"}
            <Tasks AllTasks={$tasks} label="All" />
          {:else if filter === "active"}
            <Tasks AllTasks={activeTask} label="Active" />
          {:else if filter === "completed"}
            <Tasks AllTasks={completeTask} label="Completed" />
          {/if}
        </div>
      </div>
    </div>
  {/if}
</main>
<svelte:head>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6"
    crossorigin="anonymous"
  />
  <title>My First Svelte App</title>
</svelte:head>

<style>
  main > h1 {
    text-align: center;
  }
</style>
