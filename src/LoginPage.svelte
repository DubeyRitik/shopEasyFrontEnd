<script lang="ts">
  let userid:string = "";
  let password:string = "";
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  function checkLogin():void {
    if (userid === "ritik" && password === "ritik") {
      localStorage.setItem("key", "yes");
      dispatch('loggedIn', { text: 'loggedIn' });
    } else {
      document.getElementById('message').innerHTML = "Please check id and password.";
    }
  }
</script>

<style>

</style>

<h1>Login Page</h1>
<h3 id="userid">Enter userid:</h3>
<input type="text" bind:value={userid}>
<h3 id="password">Enter password</h3>
<input type="password" bind:value={password} >
<button on:click={checkLogin}>Login</button>
<h2 id="message"></h2>
