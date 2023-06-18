<script lang="ts">
	
</script>

<style>
  .hero {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    padding: 2rem;
    background-color: #eba2a2;
    text-align: center;
  }

  .left {
    display: grid;
    grid-template-rows: 1fr 1fr;
    justify-content: center;
  }

  .left h1 {
    font-size: 5rem;
    margin-bottom: 1rem;
    color: #272525;
  }

  .left h2 {
    font-size: 2.5rem;
    color: #777;
  }

  .right {
    display: grid;
    justify-content: center;
    align-items: center;
  }

  .right img {
    height: 300px;
    max-width: 100%;
  }
</style>

<div class="hero">
  <div class="left">
    <h1>ShopEasy</h1>
    <h2>Managing shop becomes Easy.</h2>
  </div>
  <div class="right">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8e/Shop.svg/1200px-Shop.svg.png" alt="shop">
  </div>
</div>
