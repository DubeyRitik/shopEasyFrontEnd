<script lang="ts">
  import { createEventDispatcher } from 'svelte';
  import HomePage from './HomePage.svelte';
  import ToolPage from './ToolPage.svelte';
  import ContactUs from './ContactUs.svelte';
  import { fade } from 'svelte/transition';
  const dispatch = createEventDispatcher();

  function logout():void {
    localStorage.removeItem("key");
    dispatch('loggedOut', { text: 'loggedOut' });
  }

  let homeVis:boolean = false;
  let toolVis:boolean = true;
  let contactVis:boolean = false;
  function showContact():void {
    homeVis = false;
    toolVis = false;
    contactVis = true;
  }

  function showHome():void {
    homeVis = true;
    toolVis = false;
    contactVis = false;
  }

  function showTool():void {
    homeVis = false;
    toolVis = true;
    contactVis = false;
  }


</script>

<style>
  .nav {
    display: grid;
    grid-template-columns: 1fr 1fr;
    background-color: antiquewhite;
  }

  .navRight {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr ;
    font-size: large;
    justify-content: center;
    align-items: center;
  }
</style>

<div class="nav">
  <h1 transition:fade>ShopEasy</h1>
  <div class="navRight">
    <a href="#" on:click={showHome}>Home</a>
    <a href="#" on:click={showTool}>Tool</a>
    <a href="#" on:click={showContact}>Contact Us</a>
    <a href="#" on:click={logout}>Logout</a>
  </div>
</div>
 
{#if homeVis}
<HomePage></HomePage>
{/if}

{#if toolVis}
<ToolPage></ToolPage>
{/if}

{#if contactVis}
<ContactUs></ContactUs>
{/if}