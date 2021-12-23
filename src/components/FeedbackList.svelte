<script>
    import FeedbackItem from './FeedbackItem.svelte'

    // catch feedback prop from app.svelte
    export let feedback = []
</script>

{#each feedback as fb (fb.id)}
    <!-- take each item {fb} as prop -->
    <!-- don't have access to feedback list, but without the = after on:delete-feedback, can forward up to App (event forwarding) -->
    <FeedbackItem item={fb} on:delete-feedback/>
{/each}