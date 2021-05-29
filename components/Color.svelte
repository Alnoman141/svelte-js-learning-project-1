<main>
    <div class="d-flex">
        {#each colors as color}
            <div on:click="{() => selectColor(color) }" class="color mx-2 {selectedColor === color ? 'selectedColor':''}" style="background-color: {color};"></div>
        {/each}
    </div>
</main>
<script>
    let colors = ['red', 'orange', 'yellow', 'blue', 'green', 'purple'];
    export let selectedColor = 'orange';

    function selectColor(color) {
        selectedColor = color;
    }
</script>
<style>
    main .color {
        height: 50px;
        width: 50px;
        border-radius: 50%;
        cursor: pointer;
    }
    .selectedColor {
        border: 2px solid #000;
    }
</style>