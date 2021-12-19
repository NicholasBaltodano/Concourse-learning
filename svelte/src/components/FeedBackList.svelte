<script>
    import { fade } from 'svelte/transition'
    import FeedBackItem from "./feedBackItem.svelte";
 export let feedback;
</script>


{#each feedback as review}
<div transition:fade="{{duration: 100}}">
   <FeedBackItem  item={review} on:remove />   
</div>
 
{/each}

<style>  

</style>