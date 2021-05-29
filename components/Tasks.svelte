<main transition:slide>
    <div class="my-3">
        <h4>{label} Task</h4>
        {#if AllTasks.length === 0}
            <p>There is no task yet.</p>
        {:else}
        <p>Total Task: {$tasks.length} | Active Task : {$tasks.length - totalCompleted} | Completed Task: { totalCompleted }</p>
         <ul class="list-group">
            { #each AllTasks as task}
            <li class="list-group-item" on:dblclick="{e => handleEditable(e, task.id)}">
                <input type="checkbox" class="form-check-input" on:change="{e => completeTask(e, task.id)}" checked={task.isCompleted} />
                <label>{ task.isCompleted ? 'Done!' : 'Not Done!' }</label>
                <input on:keypress="{e => updateTask(e, task.id)}" type="text" bind:value={task.title} disabled={!task.isEditable} class="form-control {task.isCompleted ? 'complete' : ''}">
                <div class="color mx-3" title={task.discription} style="background-color: {task.color};">
                </div>
            </li>
            {/each}
          </ul>
        {/if}
    </div>
    
</main>
<script>
    import {slide} from 'svelte/transition'
    import { tasks } from '../src/store'
    export let AllTasks;
    export let label = 'All';

    $: totalCompleted = $tasks.filter(t => t.isCompleted).length;

    function completeTask(e, id){
        let tempTask = [...$tasks];
        let index = tempTask.findIndex(t => t.id === id);
        tempTask[index].isCompleted = e.target.checked;
        tasks.set(tempTask);
    }

    function handleEditable(e, id){
        let tempTask = [...$tasks];
        let index = tempTask.findIndex(t => t.id === id);
        tempTask[index].isEditable = true;
        tasks.set(tempTask);
    }

    function updateTask(e, id){
        if(e.key === 'Enter' && e.target.value){
            let tempTask = [...$tasks];
            let index = tempTask.findIndex(t => t.id === id);
            tempTask[index].title = e.target.value;
            tempTask[index].isEditable = false;
            tasks.set(tempTask);
        }
    }
</script>
<style>
    .complete {
        text-decoration: line-through;
    }
    .color {
        height: 5px;
    }
</style>