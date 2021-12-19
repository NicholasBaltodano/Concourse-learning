<script>
    import {v4 as uuidv4  } from "uuid";
    //import { text } from 'svelte/internal';
    import Button from './Button.svelte';
    import Card from './Card.svelte';
    import RatingSelect from './RatingSelect.svelte';
    import {createEventDispatcher} from 'svelte';

    let textPlaceHolder = "Tell us something that keeps you coming back";
    let btnDisabled =true;
    let min = 10;
    let message;
    let text = '';
    let rating = 10;
    let dispatch = createEventDispatcher();

    const  checkInput = () => {
        if(text.trim().length <= min) {
            message = `Text must be at least ${min} characters`

        }
        else {
            message = null;
            btnDisabled = false;
        }
    }

    const handleSelect= e => rating = e.detail;

    const handleSubmit = () => {
        if(text.trim().length > 10){
            const newFeedBack = {
                text, 
                rating: +rating, 
                id: uuidv4()
            }
            dispatch('newFeedBack', newFeedBack);
            text= '';
        }
        
    }
</script>


<Card>
    <header>
        <h2>How would you rate you service with us ?</h2>
    </header>
    <div class="form-wrapper">
        <RatingSelect on:ratingSelect={handleSelect}/>
        <form on:submit|preventDefault={handleSubmit}>
            <div class="input-group">
                <input type="text" bind:value={text}  on:input={checkInput} placeholder={textPlaceHolder} id="">
                <Button type="submit" disabled={btnDisabled}>Submit</Button>
                {#if message}
                <div class="message">
                    {message}
                </div>
                {/if}
            </div>
        </form>
    </div>
   
    
</Card>
<style>
    header {
      max-width: 400px;
      margin: auto;
    }
    header h2 {
      font-size: 22px;
      font-weight: 600;
      text-align: center;
    }
    .input-group {
      display: flex;
      flex-direction: row;
      border: 1px solid #ccc;
      padding: 8px 10px;
      border-radius: 8px;
      margin-top: 15px;
    }
    input {
      flex-grow: 2;
      border: none;
      font-size: 16px;
    }
    input:focus {
      outline: none;
    }
    .message{
      padding-top: 10px;
      text-align: center;
      color: rebeccapurple;
    }
    </style>