<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import { Slider } from "$lib/components/ui/slider";
  import { Textarea } from "$lib/components/ui/textarea";

  import { TextToSpeech  } from '@capacitor-community/text-to-speech';
  async function initializeTTS() {
      await TextToSpeech.initialize();
    
  }
  initializeTTS(); // Call this on component mount or initialization

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

async function handleReadMessage() {
  if (await TextToSpeech.isAvailable()) {
    try {
      await TextToSpeech.speak({
        text: message,
        // Optional options:
        // - locale: "en-US" (specify language)
        // - rate: 1 (speed of speech)
        // - pitch: 1 (pitch of voice)
        // - volume: 1 (volume of speech)
      });
    } catch (error) {
      console.error("Error speaking text:", error);
    }
  } else {
    console.warn("Text-to-Speech not available");
  }
}
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Speech Assistance</Card.Title>
    <Card.Description>Say it your way - text, gestures, or voice, we've got you covered!</Card.Description>
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
        <Button class="w-1/2" onclick={() => speak("Hey")} variant="outline">Hey</Button>
        <Button class="w-1/2" onclick={() => speak("How are you?")} variant="outline">How are you?</Button>
      </div>
      <div class="flex gap-2">
        <Button class="w-1/2" onclick={() => speak("Nice to meet you.")} variant="outline">Nice to meet you</Button>
        <Button class="w-1/2" onclick={() => speak("i love you")} variant="outline">I love you</Button>
      </div>
      <div class="flex gap-2">
        <Button class="w-1/2" onclick={() => speak("How's your day?")} variant="outline">How's your day</Button>
        <Button class="w-1/2" onclick={() => speak("Good Morning")} variant="outline">Good morning</Button>
      </div>
      <div class="flex gap-2">
        <Button class="w-1/2" onclick={() => speak("Yes")} variant="outline">Yes</Button>
        <Button class="w-1/2" onclick={() => speak("No")} variant="outline">No</Button>
      </div>
    </div>
  </Card.Content>
</Card.Root>
