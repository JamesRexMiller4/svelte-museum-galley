<script>
  import { createEventDispatcher } from 'svelte';
  import Photo from './Photo.svelte';
  const dispatch = createEventDispatcher();
  export let records;
  export let pageNum;
  let src = '../images/next.png';


  function dispatchPageNum() {
    let newNum = pageNum + 1
    dispatch('newPage', {newNum})
  }
</script>

<main>
		<header>
			<h1>Harvard's Art Museum Collection</h1>
		</header>
    <section>
      <ul class='slides'>
        {#each records as record, i}
        <input type="radio" name="radio-btn" id={`img-${i}`} checked />
          <li class="slide-container">
          <div class="slide">
            <Photo photoUrl={record.baseimageurl}/>
          </div>
          <div class="nav">
            <label for={`img-${i+1}`} class="prev">&#x2039;</label>
            <label for={`img-${i-1}`} class="next">&#x203a;</label>
          </div>
          </li>
        {/each}
      </ul>
    </section>
    <footer>
      <img {src} alt='next-arrow' on:click={dispatchPageNum}/>
    </footer>
</main>

<style>
  main {
      width: 100vw;
      height: 100vh;
      margin: 0;
      background-image: url('../images/art-gallery-background-img.jpg');
      background-repeat: no-repeat;
      background-size: cover;
    }

	header {
		height: 20vh;
	}

	h1 {
		font-family: 'Open Sans';
		color: white;
		font-size: 2.5rem;
		padding: 40px;
  }

.slides {
    padding: 0;
    width: 609px;
    height: 420px;
    display: block;
    margin: 0 auto;
    position: relative;
}
  .slides * {
    user-select: none;
    -ms-user-select: none;
    -moz-user-select: none;
    -khtml-user-select: none;
    -webkit-user-select: none;
    -webkit-touch-callout: none;
}
  .slides input { 
    display: none; 
  }

  .slide-container { 
    display: block; 
  }
  
  .slide {
    top: 0;
    opacity: 0;
    width: 609px;
    height: 420px;
    display: block;
    position: absolute;
    transform: scale(0);
    transition: all .7s ease-in-out;
    text-align: center;
  }

  .nav label {
    width: 100px;
    height: 50%;
    margin-top: 150px;
    display: none;
    position: absolute;
	  opacity: 0;
    z-index: 9;
    cursor: pointer;
    transition: opacity .2s;
    color: #FFF;
    font-size: 156pt;
    line-height: 180px;
    padding: 0px 20px;
    font-family: "Varela Round", sans-serif;
    background-color: rgba(255, 255, 255, .3);
    text-shadow: 0px 0px 15px rgb(119, 119, 119);
}

.slide:hover + .nav label { opacity: 0.5; }

.nav label:hover { opacity: 1; }

.nav .next { right: 0; }

input:checked + .slide-container  .slide {
    opacity: 1;

    transform: scale(1);

    transition: opacity 1s ease-in-out;
}

input:checked + .slide-container .nav label { display: block; }

footer {
  margin-top: 20px;
  text-align: center;
}

img {
  width: 4vw;
}
img:hover {
  cursor:pointer
}
</style>