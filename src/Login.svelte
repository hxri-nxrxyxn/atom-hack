<script>
  import Nav from "./Nav.svelte";
  import { Router, Link } from "svelte-routing";
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";

  const defaultEmail = "user@atom.com";
  const defaultPassword = "password";

  let email = localStorage.getItem("email") || defaultEmail;
  let password = "";
  let isLoggedIn = localStorage.getItem("isLoggedIn") === "true";

  function handleSubmit(event) {
    event.preventDefault();

    if (email === defaultEmail && password === defaultPassword) {
      localStorage.setItem("isLoggedIn", "true");
      isLoggedIn = true;
      location.href = "/dashboard"
    } else {
      alert("Invalid credentials!");
    }
  }
</script>

  <Nav />
  <Card.Root class="mx-auto max-w-sm">
    <Card.Header>
      <Card.Title class="text-xl">Log In</Card.Title>
      <Card.Description>Enter your information to create an account</Card.Description>
    </Card.Header>
    <Card.Content>
      <div class="grid gap-4">
        <div class="grid gap-2">
          <Label for="email">Email</Label>
          <Input
            id="email"
            type="email"
            placeholder="hari@atom.hack"
            bind:value={email}
            required
          />
        </div>
        <div class="grid gap-2">
          <Label for="password">Password</Label>
          <Input id="password" type="password" bind:value={password} />
        </div>
        <Link to="/parent">
        <Button type="submit" variant="outline" class="w-full">
          Companion Login
        </Button>
        </Link>
        <Button type="submit" class="w-full" onclick={handleSubmit}>
          Login
        </Button>
      </div>
      <div class="mt-4 text-center text-sm">
        Don't have an account?
        <Link to="/signup">
          <a class="underline">Sign Up</a>
        </Link>
      </div>
    </Card.Content>
  </Card.Root>
