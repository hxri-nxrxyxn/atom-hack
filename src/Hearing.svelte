<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import { Slider } from "$lib/components/ui/slider";
  import { Textarea } from "$lib/components/ui/textarea";

  let recognition;
  let isListening = false; // Track listening state

  function startSpeechRecognition() {
    if ('SpeechRecognition' in window || 'webkitSpeechRecognition' in window) {
      const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
      recognition = new SpeechRecognition();
      recognition.continuous = true;
      recognition.interimResults = true;

      recognition.onstart = () => {
        console.log('Speech recognition started');
        isListening = true; // Update listening state
      };

      recognition.onerror = (event) => {
        console.error('Speech recognition error:', event.error);
        document.getElementById('result').textContent = "Error occurred. Please try again.";
        isListening = false; // Update listening state
      };

      recognition.onend = () => {
        console.log('Speech recognition ended');
        recognition = null;
        isListening = false; // Update listening state
      };

      recognition.onresult = (event) => {
        let finalTranscript = '';
        let interimTranscript = '';

        for (let i = event.resultIndex; i < event.results.length; ++i) {
          if (event.results[i].isFinal) {
            finalTranscript += event.results[i][0].transcript;
          } else {
            interimTranscript += event.results[i][0].transcript;
          }
        }

        document.getElementById('result').textContent = finalTranscript;
      };

      recognition.start();
    } else {
      document.getElementById('result').textContent = 'Your browser does not support the Web Speech API';
    }
  }

  function stopSpeechRecognition() {
    if (recognition) {
      recognition.stop();
      recognition = null;
    }
  }
</script>

<Nav/>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Hearing</Card.Title>
    <Card.Description>Hearing with ease</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Button on:click={isListening ? stopSpeechRecognition : startSpeechRecognition} class="w-full">
          {isListening ? "Stop Listening" : "Listen"}
        </Button>
      </div>
      <div class="grid gap-2">
        <Label for="email">Result Message</Label>
        <Button id="result" type="submit" variant="secondary" class="h-40 w-full">Result</Button>
      </div>
    </div>
  </Card.Content>
</Card.Root>
