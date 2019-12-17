<script>
  export let text = "test";
  export let instructions = false;
</script>

<style>
  h1 {
    margin: 0;
  }
  section {
    height: 100vh;
    max-height: 60%;
    width: 100%;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #1d1d1d;
    color: white;
    text-align: center;
  }

  .instructions {
    display: block;
    position: absolute;
    left: 50%;
    bottom: 4.5rem;
    transform: translate(-50%, -50%);
    text-align: center;
  }
  figure {
    display: block;
    transform: rotate(135deg);
    border: 1px solid transparent;
    border-top-color: white;
    border-right-color: white;
    width: 12px;
    height: 12px;
    margin: 0 auto;
  }

  span {
    display: block;
    margin: 0 auto;
    text-transform: uppercase;
    font-size: 0.5rem;
    letter-spacing: 0.2rem;
  }
</style>

<section>
  <h1>{text}</h1>
  {#if instructions}
    <div class="instructions">
      <span>scroll down</span>
      <figure />
    </div>
  {/if}
</section>
