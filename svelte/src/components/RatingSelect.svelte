<script>
    import {createEventDispatcher} from 'svelte';

    let numbers = [1,2,3,4,5,6,7,8,9,10] ;
    let selected = 10;

    let dispatch = createEventDispatcher();

    const onChange = (e) =>
    {
        selected = e.currentTarget.value;
        dispatch('ratingSelect', selected);
    }
</script>


 <!-- rating-->
 <ul class="rating">
    {#each numbers as number}
    <li>
        <input type="radio" id="{'num' + number}" name="rating" value={number}
        on:change={onChange} checked={selected===number}/>
        <label for="{'num' + number}">{number}</label>
        </li>
    
    {/each}
 </ul>



 <style>
     
  .rating {
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin: 30px 0;
  }
  .rating li {
    position: relative;
    background: #f4f4f4;
    width: 50px;
    height: 50px;
    padding: 10px;
    text-align: center;
    border-radius: 50%;
    font-size: 19px;
    border: 1px #eee solid;
    transition: 0.3s;
  }
  .rating li label {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 50px;
    height: 50px;
    padding: 10px;
    border-radius: 50%;
    transform: translate(-50%, -50%);
    cursor: pointer;
  }
  .rating li:hover {
    background: #ff6a95;
    color: #fff;
  }
  /* Make actual radio select invisible */
  [type='radio'] {
    opacity: 0;
  }
  /* Use the sibling select */
  [type='radio']:checked ~ label {
    background: #ff6a95;
    color: #fff;
  }

 </style>