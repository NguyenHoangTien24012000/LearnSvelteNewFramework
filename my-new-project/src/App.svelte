<script>
	import FeedbackList from './components/FeedbackList.svelte';
	import FeedBackStats from './components/FeedbackStats.svelte';
	import FeedBackForm from './components/FeedBackForm.svelte';
	import Day1 from './LearnSvelte/App1.svelte';
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
	const addFeedback = (e) =>{
		// console.log(e)
		feedback = [e.detail,...feedback]
	}
</script>

<main class="container">
	<!-- <FeedBackForm on:add-feedback={addFeedback} />
	<FeedBackStats {count} {average} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback} /> -->
		<Day1 />

</main>

<style>

</style>
