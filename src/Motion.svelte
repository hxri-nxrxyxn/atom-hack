<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import { Slider } from "$lib/components/ui/slider";
  import { Textarea } from "$lib/components/ui/textarea";
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Motion</Card.Title>
    <Card.Description>let's make them know our necessities</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Button type="submit" variant="outline" class="w-full">Go to bathroom</Button>
        <Button type="submit" variant="outline" class="w-full">Need food</Button>
        <Button type="submit" variant="outline" class="w-full">Turn me over</Button>
      </div>
    </div>
  </Card.Content>
</Card.Root>

