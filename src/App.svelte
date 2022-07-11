<script>
  import Content from './components/template/Content.svelte';
  import Navbar from './components/template/Navbar.svelte';
  import Home from './pages/Home.svelte';
</script>

<main>
  <Navbar />
  <Content><Home /></Content>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
</style>
