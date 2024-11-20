<script>
    import { onMount } from 'svelte';
    import Talk from 'talkjs';

    onMount(() => {
    Talk.ready.then(() => {
        const session = new Talk.Session({
        appID: 'YOUR_APP_ID',
        me: currentUser,
    });
  });
});

  let chatboxEl;
  </script>

<main>
    <div bind:this={chatboxEl}></div>
  </main>