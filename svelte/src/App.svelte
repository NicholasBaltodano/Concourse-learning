<script>
	import FeedBackList from './components/FeedBackList.svelte'
  import Average from './components/average.svelte'
import FeedbackForm from './components/FeedbackForm.svelte';
import { text } from 'svelte/internal';


let feedback = [
  {
    id: 1,
    rating: 10,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  },
  {
    id: 2,
    rating: 9,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  },
  {
    id: 3,
    rating: 8,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  },
]

$: count = feedback.length;
$: average = feedback.reduce((a, {rating}) => a + rating, 0) / count;

const remove = (e) => {
  console.log('made it')
  let itemId = e.detail; 
  feedback =  feedback.filter((item) => item.id != itemId);
}


const newFeedBack = (e) => {
  let newFeedBack = {
    id : e.detail.id,
    rating: e.detail.rating,
    text: e.detail.text
   }
  feedback = [...feedback, newFeedBack]
  feedback = feedback;

console.log(e.detail)
console.log(feedback)
}
</script>

<main class="container">
<FeedbackForm on:newFeedBack={newFeedBack}/>
<Average AverageValue={average} Count={count}/>
<FeedBackList feedback={feedback} on:remove="{remove}"/>
</main>










