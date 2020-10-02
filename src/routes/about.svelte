<script context="module">
  export async function preload({ params }) {
    // the `slug` parameter is available because
    // this file is called [slug].svelte
    const res = await this.fetch(`/api/message`);
    const data = await res.json();

    if (res.status === 200) {
      return { message: data };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  export let message;
</script>

<svelte:head>
  <title>About</title>
</svelte:head>

<h1>About this site</h1>

<p>This is the 'about' page. There's not much here.</p>
<p>Message: {message.text}</p>
