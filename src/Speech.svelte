<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import { Slider } from "$lib/components/ui/slider";
  import { Textarea } from "$lib/components/ui/textarea";

  let message = "";

function speak(text) {
  if ('speechSynthesis' in window) {
    const msg = new SpeechSynthesisUtterance();
    msg.text = text;

    // Voice selection (improved):
    const voices = window.speechSynthesis.getVoices();
    const preferredVoice = voices.find(voice => voice.lang.includes("en-US")) || voices[0]; // Fallback to first voice
    if (preferredVoice) {
      msg.voice = preferredVoice;
    }

    window.speechSynthesis.speak(msg);
  } else {
    alert('Your browser does not support the Web Speech API');
  }
}

function handleTextAreaChange(event) {
  message = event.target.value;
}

function handleReadMessage() {
  speak(message);
}
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Speech</Card.Title>
    <Card.Description>Let's connect with ease</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Label for="email">Message</Label>
        <Textarea placeholder="Enter your message here" bind:value={message}/>
      </div>
      <div class="grid gap-2">
        <Button type="submit" onclick={handleReadMessage} class="h-40 w-full">Read the message</Button>
      </div>
    </div>
  </Card.Content>
</Card.Root>

<br>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Quick Play</Card.Title>
    <Card.Description>Let's connect faster</Card.Description>
  </Card.Header>
  <Card.Content>

    <div class="grid gap-2">
      <div class="flex gap-2">
        <Button class="w-1/3" onclick={() => speak("Hey")} variant="outline">Hey</Button>
        <Button class="w-1/3" onclick={() => speak("How are you?")} variant="outline">How are you?</Button>
        <Button class="w-1/3" onclick={() => speak("Good Morning")} variant="outline">Good morning</Button>
      </div>
      <div class="flex gap-2">
        <Button class="w-1/3" onclick={() => speak("Nice to meet you.")} variant="outline">Nice to meet you</Button>
        <Button class="w-1/3" onclick={() => speak("i love you")} variant="outline">I love you</Button>
        <Button class="w-1/3" onclick={() => speak("thank you")} variant="outline">Thank you</Button>
      </div>
      <div class="flex gap-2">
        <Button class="w-1/3" onclick={() => speak("How's your day?")} variant="outline">How's your day</Button>
        <Button class="w-1/3" onclick={() => speak("Yes")} variant="outline">Yes</Button>
        <Button class="w-1/3" onclick={() => speak("No")} variant="outline">No</Button>
      </div>
    </div>
  </Card.Content>
</Card.Root>
