<script lang="ts">
  import LoginPage from "./LoginPage.svelte";
  import MainPage from "./MainPage.svelte";

  let isLogged: string | null = localStorage.getItem('key');

  function handleMessage(event: { detail: { text: string } }) {
    if (event.detail.text === 'loggedOut') {
      isLogged = null;
    }
  }

  function loginFun(event: { detail: { text: string } }) {
    if (event.detail.text === 'loggedIn') {
      isLogged = "yes";
    }
  }
</script>

<style>

</style>

{#if isLogged !== null}
  <MainPage on:loggedOut={handleMessage}/>
{:else}
  <LoginPage on:loggedIn={loginFun}/> 
{/if}
