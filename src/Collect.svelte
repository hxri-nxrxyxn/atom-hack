<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import * as DropdownMenu from "$lib/components/ui/dropdown-menu";
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Tell us about yourself</Card.Title>
    <Card.Description>Your information will be safe with us</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Label for="email">Age</Label>
        <Input id="email" type="email" placeholder="69" required />
      </div>
      <div class="gap-2">
        <Label for="password">Blood Group</Label>
        <br>
        <DropdownMenu.Root>
          <DropdownMenu.Trigger class="w-full">
            <Button variant="outline" class="w-full">choose a blood group</Button>
          </DropdownMenu.Trigger>
          <DropdownMenu.Content>
            <DropdownMenu.Group>
              <DropdownMenu.Label>Choose</DropdownMenu.Label>
              <DropdownMenu.Separator />
              <DropdownMenu.Item>A+</DropdownMenu.Item>
              <DropdownMenu.Item>A-</DropdownMenu.Item>
            </DropdownMenu.Group>
          </DropdownMenu.Content>
        </DropdownMenu.Root>
      </div>
      <div class="grid gap-2">
        <Label for="password">Emergency Contact</Label>
        <Input id="password" placeholder="+91 12345 67890"/>
      </div>
      <Link to="/issues">
        <Button type="submit" class="w-full">Continue</Button>
      </Link>
    </div>
  </Card.Content>
</Card.Root>
