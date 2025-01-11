<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import { Checkbox  } from "$lib/components/ui/checkbox/index.js";
  import * as DropdownMenu from "$lib/components/ui/dropdown-menu";

  function speak(text) {
    if ('speechSynthesis' in window) {
        const utterance = new SpeechSynthesisUtterance(text);
        speechSynthesis.speak(utterance);
    } else {
        alert('Your browser does not support the Web Speech API.');
    }
}

async function speakArrayWithDelay(textArray, delay = 5000) {
    for (const text of textArray) {
        speak(text);
        await new Promise(resolve => setTimeout(resolve, delay)); // Wait for the delay
    }
}



const somefunc = async () => {
    const textArray = [
        " ",
        "Enter your age and blood group",
        "also tell us your emergency and personal contact numbers",
      "We'll need your height and weight ",
      "Enter allergies, medical conditions, medications, if any",
      "Do you have any accessibility needs"
    ];
    try {
        await speakArrayWithDelay(textArray);
    } catch (error) {
        console.error("An error occurred:", error);
        alert("An error occurred during speech.");
    }
};
  somefunc();
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
              <DropdownMenu.Item>O+</DropdownMenu.Item>
              <DropdownMenu.Item>O-</DropdownMenu.Item>
              <DropdownMenu.Item>B+</DropdownMenu.Item>
              <DropdownMenu.Item>B-</DropdownMenu.Item>
              <DropdownMenu.Item>AB+</DropdownMenu.Item>
              <DropdownMenu.Item>AB-</DropdownMenu.Item>
            </DropdownMenu.Group>
          </DropdownMenu.Content>
        </DropdownMenu.Root>
      </div>
      <div class="grid gap-2">
        <Label for="password">Emergency Contact</Label>
        <Input id="password" placeholder="+91 12345 67890"/>
      </div>
      <div class="grid gap-2">
        <Label for="password">Personal Number</Label>
        <Input id="password" placeholder="+91 12345 67890"/>
      </div>
      <div class="grid gap-2">
        <Label for="password">Height</Label>
        <Input id="password" placeholder="193cm"/>
      </div>
      <div class="grid gap-2">
        <Label for="password">Weight</Label>
        <Input id="password" placeholder="58kg"/>
      </div>
      <div class="grid gap-2">
        <Label for="password">Allergy</Label>
        <Input id="password" placeholder="None"/>
      </div>
      <div class="grid gap-2">
        <Label for="password">Medical Conditions</Label>
        <Input id="password" placeholder="None"/>
      </div>
      <div class="grid gap-2">
        <Label for="password">Current Medication</Label>
        <Input id="password" placeholder="None"/>
      </div>
      <div class="grid gap-2">
        <Label for="password">Accessibility Needs</Label>
        <div class="flex gap-2">
          <Checkbox id="terms"  aria-labelledby="terms-label" />
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Visual
          </Label>
        </div>
        <div class="flex gap-2">
          <Checkbox id="terms"  aria-labelledby="terms-label" />
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Speech
          </Label>
        </div>
        <div class="flex gap-2">
          <Checkbox id="terms"  aria-labelledby="terms-label" />
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Hearing
          </Label>
        </div>
        <div class="flex gap-2">
          <Checkbox id="terms"  aria-labelledby="terms-label" />
          <Label
            id="terms-label"
            for="terms"
            class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
          >
            Speech
          </Label>
        </div>
      </div>
      <Link to="/">
        <Button type="submit" class="w-full">Continue</Button>
      </Link>
    </div>
  </Card.Content>
</Card.Root>
