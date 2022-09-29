<script>
  import { page } from "$app/stores";
  import "../styles/global.css";
</script>

<div class="error">
  <h1>{$page.status}: {$page.error.message}</h1>
  <a href="/guides">View all guides</a>
</div>

<style>
  .error {
    text-align: center;
    margin-bottom: 60px;
  }
</style>
