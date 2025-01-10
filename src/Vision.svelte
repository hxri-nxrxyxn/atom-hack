<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import { Slider } from "$lib/components/ui/slider";
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Vision</Card.Title>
    <Card.Description>Do quick actions with limited vision</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Button type="submit" variant="outline" class="h-40 w-full">1. Do this</Button>
        <Button type="submit" class="h-40 w-full">Read aloud actions</Button>
      </div>
    </div>
  </Card.Content>
</Card.Root>