<script>
	import FeedbackList from './components/FeedbackList.svelte';
	import FeedBackStats from './components/FeedbackStats.svelte';
	import FeedBackForm from './components/FeedBackForm.svelte';
	let feedback = [
		{
			id : 1,
			rating : 10,
			text : 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Deserunt aperiam eum eius dolorem voluptas cupiditate dolores voluptate beatae fugiat corrupti.'
		},
		{
			id : 2,
			rating : 9,
			text : 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Deserunt aperiam eum eius dolorem voluptas cupiditate dolores voluptate beatae fugiat corrupti.'
		},
		{
			id : 3,
			rating: 8,
			text : 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Deserunt aperiam eum eius dolorem voluptas cupiditate dolores voluptate beatae fugiat corrupti.'
		}
	]
	
	$: count = feedback.length;
	$: average = count === 0 ? 0 : feedback.reduce((a, {rating}) => a + rating, 0) / count;

	const deleteFeedback = (e) =>{
		console.log(e.detail)
		const itemId = e.detail;
		feedback = feedback.filter(item => item.id != itemId);
	}
</script>

<main class="container">
	<FeedBackForm />
	<FeedBackStats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} />

</main>

<style>

</style>
