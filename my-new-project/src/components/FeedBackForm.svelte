<script>
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import RatingSelect from './RatingSelect.svelte';
  let text = "";
  let btnDisabled = true;
  let min = 10;
  let rating = 10;
  let message;
  const handleInput =() =>{
    if(text.trim().length <= min){
        message = `Text must be at least ${min} characters`
        btnDisabled = true;
    }else{
        message = null;
        btnDisabled = false;
    }
  }
</script>

<Card>
  <header>
    <h2>How would you rate your service with us?</h2>
  </header>
  <RatingSelect />
  <form>
    <div class="input-group">
      <input on:input={handleInput}
        type="text"
        bind:value={text}
        placeholder="Tell us something that keeps you coming back"
      />
      <Button disabled={btnDisabled} type="submit">Send</Button>
    </div>
    {#if message}
        {message}
    {/if}
  </form>
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
    width: 80%;
    margin:15px auto 0;
    margin-top: 15 px;
  }
  input {
    flex-grow: 2;
    width: 100px;
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
