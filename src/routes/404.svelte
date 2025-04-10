<script>
  import { page } from '$app/stores';
</script>

<h1>Page Not Found</h1>
<p>Could not find {$page.url.pathname}</p>
<a href="/">Return home</a>

<style>
  h1 { color: #dc3545; }
  a { color: #3498db; }
</style>