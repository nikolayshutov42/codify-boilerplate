<script>
  export let status
  export let error
  let isJoining = true
  let showError = false
  let loading = true
  import { onMount } from 'svelte'

  onMount(async () => {
    try {
      const shortlink = window.location.pathname.split('/')[1]
      if (shortlink) {
        const res = await fetch(`https://api.holoclinic.io/appointment/short/${shortlink}`)
        if (res.status > 300) {
          throw new Error('no link found')
        }
		isJoining = true;
        const link = await res.json()
        window.location.href = `https://app.holoclinic.io/call/${link.joinToken}`
      }
      loading = false
    } catch (error) {
      loading = false
      showError = true
      isJoining = false
      console.log(error)
    }
  })

  const dev = process.env.NODE_ENV === 'development'
</script>

<svelte:head>
  <title>{status}</title>
</svelte:head>

<section class="hero is-fullheight bg">
  <div class="hero-body">
    <div class="container has-text-centered">
      {#if loading}
        <p>LOADING</p>
      {/if}

	  {#if !loading && isJoining}
        <p>Please wait. You'll be redirected shortly</p>
      {/if}

      {#if showError}
        <div class="error-page">
          <h1 class="title is-size-1">{status}</h1>
          <img src="/img/404.gif" alt="Not Found" />
          <p class="subtitle">{error.message}</p>
        </div>
        {#if dev && error.stack}
          <pre>{error.stack}</pre>
        {/if}
      {/if}
    </div>
  </div>
</section>

<style>
  .bg {
    background: #fcfefc;
  }
</style>
