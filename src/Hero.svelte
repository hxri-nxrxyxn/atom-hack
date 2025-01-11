<script>
  import {Router, Link} from "svelte-routing"
  import Nav from "./Nav.svelte"
  import * as Card from "$lib/components/ui/card/index.js";
  import { Button } from "$lib/components/ui/button/index.js";

  fetch('http://175.20.1.151:5555/send-data')
  .then(r => r.text())
  .then(text => console.log(text));
</script>

<main>
  <div class="heading">
    <div class="heading__box">
      <h1>ATOM</h1>
    </div>
    <p>Enable. Empower. Elevate</p>
  </div>
  <div class="grid gap-2">
      <Link to="/login">
        <Button type="submit" class="w-full">Login</Button>
      </Link>
      <Link to="/emergency">
        <Button variant="outline" href="/login" type="submit" class="w-full">Emergency</Button>
      </Link>
  </div>
</main>

  <style>
  .heading {
    height: 70vh;
  }
  .heading__box {
    height: 40vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  h1 {
    font-size: 5rem;
    font-weight: 700;
    color: hsl(var(--primary) / var(--tw-bg-opacity, 1));
  }
  h1, p {
    font-family: "Inter";
  }
  p {
    color: #666;
    text-align: center;
    font-weight: 300;
  }
  </style>
