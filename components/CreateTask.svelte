<script context="module">
  import {slide} from 'svelte/transition'
  import {tasks} from '../src/store.js';
  // import { createEventDispatcher } from 'svelte';
  import Color from "./Color.svelte";
</script>

<script>

  // normal way
  // let dispatcher = createEventDispatcher();

  let title = "";
  let discription = "";
  let color = "";

  function taskSubmited(e){
      if(!title){
          alert('Please Provide a Title');
          return
      } else {
          let id = ( Math.random() * new Date().getTime()).toString();
          let task = {
            id,
            title,
            discription,
            color,
            isCompleted: false,
            isEditable: false
          }
          // dispatcher('taskCreated', task)
          let newTask = [task, ...$tasks];
          tasks.set(newTask);
          e.target.reset();
          color = '';
      }
  }
</script>

<main transition:slide>
  <div class="row">
    <div class="col-md-6 offset-md-3">
      <div class="card card-body">
        <form on:submit|preventDefault={taskSubmited}>
            <div class="mb-3">
                <label for="title" class="form-label">Task Title</label>
                <input
                  bind:value={title}
                  type="text"
                  class="form-control"
                  id="title"
                  placeholder="enter your task title"
                />
              </div>
              <div class="mb-3">
                <label for="desc" class="form-label">Discription</label>
                <textarea
                  bind:value={discription}
                  class="form-control"
                  id="disc"
                  rows="3"
                />
              </div>
              <div class="my-3">
                <Color bind:selectedColor={color} />
              </div>
              <div class="mt-3 mx-auto">
                <input type="submit" class="btn btn-dark" value="Submit">
              </div>
        </form>
      </div>
    </div>
  </div>
</main>
