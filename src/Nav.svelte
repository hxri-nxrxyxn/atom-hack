<script>
    import {Route, Router, Link} from 'svelte-routing'
  </script>


<main>
  <Link to="/">
      <h1>ATOM</h1>
    </Link>
</main>

  <style>
  main {
    text-align: center;
    margin-bottom: 1rem;
  }
  h1 {
    font-size: 2rem;
    font-weight: 700;
    color: hsl(var(--primary) / var(--tw-bg-opacity, 1));
  }
  </style>
