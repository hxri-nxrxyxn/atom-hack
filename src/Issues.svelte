<script>
  import Nav from "./Nav.svelte"
  import { Checkbox } from "$lib/components/ui/checkbox";
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";

  export let countboy = 1;
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Choose the issues that bother you</Card.Title>
    <Card.Description>I have problems with</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <div class="flex items-center space-x-2">
          <Checkbox/>
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Vision
          </Label>
        </div>
        <div class="flex items-center space-x-2">
          <Checkbox/>
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Hearing
          </Label>
        </div>
        <div class="flex items-center space-x-2">
          <Checkbox/>
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Speech
          </Label>
        </div>
        <div class="flex items-center space-x-2">
          <Checkbox/>
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Mobility
          </Label>
        </div>
  </div>
  <Link to="/dashboard">
    <Button type="submit" class="w-full">Continue</Button>
  </Link>
</div>
  </Card.Content>
</Card.Root>

