<script>
    import Card from "./Card.svelte";
    import Button from "./Button.svelte";

    let text = "";
    let btnDisabled = true
    let minLength = 10
    let message

    // check length of feedback input
    const handleInput = () => {
        if (text.trim().length <= minLength) {
            message = `Text must be at least ${minLength} characters`
            btnDisabled = true
        } else {
            message = null
            btnDisabled = false
        }
    }
</script>

<Card>
    <header>
        <h2>How would you rate our service?</h2>
    </header>
    <form>
        <!-- rating selector -->
        <div class="input-group">
            <input type="text" on:input={handleInput} bind:value= {text} placeholder="Tell us what you think" />
            <Button disabled={btnDisabled} type="submit">Send</Button>
        </div>
        {#if message}
            <div class="message">
                {message}
            </div>
        {/if}
    </form>
</Card>

<style>
</style>
