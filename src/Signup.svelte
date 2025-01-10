<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Sign Up</Card.Title>
    <Card.Description>Enter your information to create an account</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid grid-cols-2 gap-4">
        <div class="grid gap-2">
          <Label for="first-name">First name</Label>
          <Input id="first-name" placeholder="Hari" required />
        </div>
        <div class="grid gap-2">
          <Label for="last-name">Last name</Label>
          <Input id="last-name" placeholder="Narayan" required />
        </div>
      </div>
      <div class="grid gap-2">
        <Label for="email">Email</Label>
        <Input id="email" type="email" placeholder="hari@atom.hack" required />
      </div>
      <div class="grid gap-2">
        <Label for="password">Password</Label>
        <Input id="password" type="password" />
      </div>
      <Link to="/collect">
        <Button type="submit" class="w-full">Create an account</Button>
      </Link>
    </div>
    <div class="mt-4 text-center text-sm">
      Already have an account?
      <Link to="/login">
        <a class="underline"> Sign in </a>
      </Link>
    </div>
  </Card.Content>
</Card.Root>

