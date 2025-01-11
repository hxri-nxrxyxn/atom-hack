<script>
  import Nav from "./Nav.svelte"
  import * as RadioGroup from "$lib/components/ui/radio-group/index.js";
  import { Checkbox } from "$lib/components/ui/checkbox";
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  const storeChoice = () => {
    localStorage.setItem("choice", i);  
  }
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
<RadioGroup.Root value="comfortable">
  <div class="flex items-center space-x-2">
    <RadioGroup.Item value="default" id="r1" />
    <Label for="r1">Vision</Label>
  </div>
  <div class="flex items-center space-x-2">
    <RadioGroup.Item value="comfortable" id="r2" />
    <Label for="r2">Motion</Label>
  </div>
  <div class="flex items-center space-x-2">
    <RadioGroup.Item value="compact" id="r3" />
    <Label for="r3">Hearing</Label>
  </div>
  <div class="flex items-center space-x-2">
    <RadioGroup.Item value="compactx" id="r4" />
    <Label for="r3">Speech</Label>
  </div>
  <RadioGroup.Input name="spacing" />
</RadioGroup.Root>
  </div>
  <Link to="/dashboard">
    <Button type="submit" class="w-full">Continue</Button>
  </Link>
</div>
  </Card.Content>
</Card.Root>

