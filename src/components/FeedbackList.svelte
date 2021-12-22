<script>
    import FeedbackItem from './FeedbackItem.svelte'

    // catch feedback prop from app.svelte
    export let feedback = []
</script>

{#each feedback as fb (fb.id)}
    <!-- take each item {fb} as prop -->
    <FeedbackItem item={fb} />
{/each}