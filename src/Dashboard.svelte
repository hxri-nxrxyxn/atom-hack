<script>
  import { fade } from 'svelte/transition';
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import { Slider } from "$lib/components/ui/slider";
  import { Textarea } from "$lib/components/ui/textarea";
</script>

<main transition:fade={{ duration: 600 }}>
<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Hearing</Card.Title>
    <Card.Description>Hearing with ease</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Link to="/vision">
          <Button type="submit" variant="outline" class="w-full">Vision</Button>
        </Link>
        <Link to="/hearing">
          <Button type="submit" variant="outline" class="w-full">Hearing</Button>
        </Link>
        <Link to="/motion">
          <Button type="submit" variant="outline" class="w-full">Motion</Button>
        </Link>
        <Link to="/speech">
          <Button type="submit" variant="outline" class="w-full">Speech</Button>
        </Link>
      </div>
    </div>
  </Card.Content>
</Card.Root>
</main>
