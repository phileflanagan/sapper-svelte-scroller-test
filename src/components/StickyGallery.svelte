<script>
  import { onMount } from "svelte";
  export let imageCount = 0;
  export let basePath = "/";
  import Scroller from "@sveltejs/svelte-scroller";
  let index, offset, progress;
</script>

<style>
  .bar {
    position: absolute;
    width: 50%;
    height: 10px;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 999999;
  }
  .progress {
    background-color: lightgreen;
    height: 100%;
    width: 0;
  }
  section {
    margin: 0;
    color: white;
    height: 100vh;
    width: 50%;
    margin-left: 50%;
    background-color: #888;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  section div {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 80%;
    height: 80%;
    text-align: center;
  }
  .background {
    position: absolute;
    top: 0;
    left: 0;
    width: 50%;
    height: 100vh;
    background-color: red;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: top center;
    transition: opacity 200ms ease-out;
  }

  /* .debugger {
    position: fixed;
    z-index: 999;
    top: 0;
    left: 0;
    padding: 0.5rem;
    color: white;
    background-color: rgba(0, 0, 0, 0.5);
  } */
</style>

<!-- <div class="debugger">
  <div>Index: {index}</div>
  <div>Offset: {offset}</div>
  <div>Progress: {progress}</div>
</div> -->

<Scroller
  top={0}
  bottom={1}
  threshold={0.5}
  bind:index
  bind:offset
  bind:progress>
  <div slot="background">
    {#if progress >= 0 && progress <= 1}
      <div class="bar">
        <div class="progress" style="width: {progress * 100}%" />
      </div>
    {/if}
    {#each Array(imageCount) as _, i}
      <div
        style="background-image: url({basePath}{i + 1}.jpg); opacity: {i <= index ? 1 : 0}"
        class="background" />
    {/each}
  </div>
  <div slot="foreground">
    <section>
      <div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Tenetur facilis
        quas quia tempore perspiciatis suscipit aliquam deleniti fugiat
        aspernatur beatae tempora odit quisquam quo eaque commodi, et amet
        dignissimos ea.
      </div>
    </section>
    <section>
      <div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorum dolore
        incidunt a illo ipsa assumenda rem! Voluptas, cum reiciendis officia et
        veritatis accusamus ducimus nemo perferendis expedita sequi eveniet quos
        animi recusandae architecto illo, laboriosam atque qui doloribus
        repudiandae quaerat quisquam velit. Incidunt culpa reiciendis molestias
        unde quisquam, deleniti quo.
      </div>
    </section>
    <section>
      <div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Eligendi quis
        quisquam veniam quidem, in necessitatibus voluptatum unde porro
        molestias nisi quo architecto temporibus cumque totam corporis earum
        maiores commodi eveniet cum. Accusantium nam quod quos tempora optio
        voluptates, impedit eligendi? Hic dicta distinctio, facere architecto
        incidunt a consequatur voluptatibus cupiditate.
      </div>
    </section>
    <section>
      <div>
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Unde at
        similique sequi molestias sit quas ipsum nihil ab deserunt delectus?
      </div>
    </section>
  </div>
</Scroller>
