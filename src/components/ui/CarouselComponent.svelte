<script>
  import { onMount } from 'svelte';

  let Carousel; // for saving Carousel component class
  let carousel; // for calling methods of the carousel instance
  onMount(async () => {
    const module = await import('svelte-carousel');
    Carousel = module.default;
  });

  const handleNextClick = () => {
    carousel.goToNext()
  }

  </script>

  <style>
    .carousel-img {
      width: 70%;
      height: max-content;
      border-radius: 15px;
      -webkit-box-shadow: 5px 5px 15px 5px #000000;
      box-shadow: 5px 5px 15px 5px rgba(0, 0, 0, 0.18);
      margin: 20px;
    }
  </style>
  <div class="slide-box">
    <svelte:component
            this={Carousel}
            bind:this={carousel}
    >
      <div class="flex centered"><img class="carousel-img" src="assets/images/carousel/1-min.png" /></div>
      <div class="flex centered"><img class="carousel-img" src="assets/images/carousel/2-min.png" /></div>
      <div class="flex centered"><img class="carousel-img" src="assets/images/carousel/3-min.png" /></div>
      <div class="flex centered"><img class="carousel-img" src="assets/images/carousel/4-min.png" /></div>
      <div class="flex centered"><img class="carousel-img" src="assets/images/carousel/5-min.png" /></div>
      <div class="flex centered"><img class="carousel-img" src="assets/images/carousel/6-min.png" /></div>
    </svelte:component>
  </div>
