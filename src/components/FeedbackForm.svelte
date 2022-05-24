<script>
    import Card from "./Card.svelte";
    import Button from "./Button.svelte";

    let text = "";
    let btnDisabled = true;
    let min = 10;
    let message;

    const handleInput = () => {
        if(text.trim().length <= min) {
            message = `Text Must Be At Least ${min} Characters`;
            btnDisabled = true;
        } else {
            message = null;
            btnDisabled = false;
        }
    }
</script>

<Card>
    <header>
        <h2>How Would You Rate Your Service With Us ?</h2>
    </header>
    <form>
        <!-- Rating Select -->
        <div class="input-group">
            <input
                type="text"
                placeholder="Tell Us Something That Keeps You Coming Back"
                bind:value={text}
                on:input={handleInput}
            />
            <Button type="submit" disabled={btnDisabled}>Send</Button>
        </div>
    </form>
    {#if message} 
        <div class="message">
            {message}
        </div>
    {/if}
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

    .message {
        padding-top: 10px;
        text-align: center;
        color: rebeccapurple;
    }
</style>
