<script>
    export let AverageValue;
    export let Count;
</script>

<div class="feedback-stats; flex">
     {#if Count != 0}
     <h4>The average is {AverageValue}</h4>
     {:else}
     <h4>No Average</h4>
    {/if}
    <h4>The count is {Count}</h4>
</div>

<style>
.feedback-stats {
    background-color: #ffff;
    border-radius: 15px;
    padding: 40px 50px;
    margin: 20px 0;
    position: relative;
    color: #333;
}

.flex {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    align-items: center;
}
</style>