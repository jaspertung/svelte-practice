<script>
	import FeedbackForm from './components/FeedbackForm.svelte'
	import FeedbackList from './components/FeedbackList.svelte'
	import FeedbackStats from './components/FeedbackStats.svelte'

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
		},
		{
			id: 2,
			rating: 9,
			text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
		},
		{
			id: 3,
			rating: 8,
			text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
		},
	];

	// reactive number for total feedback items
	$: count = feedback.length
	// test test test

	// avg of reviews
	$: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length

	// dispatch from FeedbackItem to FeedbackList which is forwarding to App
	const deleteFeedback = (e) => {
		// fetch itemId from FeedbackItem through e (event parameter)
		const itemId = e.detail
		// filter out from list when deleted
		feedback = feedback.filter((item) => item.id != itemId)
	}
</script>

<main class="container">
	<FeedbackForm />
	<FeedbackStats {count} {average}/>
	<!-- pass in {feedback} as prop, but same name so only need {} -->
	<!-- on:delete-feedback- catch event forwarding from FeedbackList and {deleteFeedback} calls the function -->
	<FeedbackList {feedback} on:delete-feedback= {deleteFeedback}/>
</main>

<style>
</style>
