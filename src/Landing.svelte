<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  export let user;
  let src = '../images/harvard-logo.png'

  function toggleEnter() {
    dispatch('toggle', {
      user: !user.hasEntered
    })
  }
</script>

<main>
  <header>
    <img {src} alt='harvard-logo'/>
  </header>
  <section>
    <h2>CLICK ENTER TO VIEW COLLECTIONS</h2>
    <button type='button' on:click={toggleEnter}>ENTER</button>
  </section>
</main>

<style>
  main {
		width: 100vw;
		height: 100vh;
		margin: 0;
		background-image: url('../images/harvard-library.jpeg');
		background-repeat: no-repeat;
		background-size: 100vw 100vh;
  }

  header {
    height: 40vh;
  }

  section {
    margin: 0 auto;
    text-align: center;
  }
  
  img {
    width: 20vw;
    margin: 20px;
  }

  h2 {
    font-size: 2rem;
    color: rgb(229, 229, 229);
  }

  button {
    width: 10vw;
    height: 5vh;
    font-family: 'Open Sans';
    border-radius: 5%;
    margin: 5px;
  }

  button:hover {
    background-color: maroon;
    color: white;
    border: 1px solid maroon;
    cursor: pointer;
  }
</style>