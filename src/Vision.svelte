<script>
  import Nav from "./Nav.svelte";
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { onMount } from 'svelte';

  let tasks = [
    "Task 1: Walk forward",
    "Task 2: Turn left",
    "Task 3: Pick up the object",
    "Task 4: Place it on the table",
  ];
  let currentTaskIndex = 0;
  let currentTask = tasks[currentTaskIndex];
  let timer;
  let synth;
    let isSpeaking = false;

    onMount(() => {
        synth = window.speechSynthesis;
    })

  function nextTask() {
    clearTimeout(timer);
    currentTaskIndex++;
    if (currentTaskIndex < tasks.length) {
      currentTask = tasks[currentTaskIndex];
        speak(currentTask)
      startTimer();
    } else {
      currentTask = "All tasks completed!";
        speak(currentTask)
    }
  }

  function handleYes() {
    if (timer) {
      clearTimeout(timer);
    }
    if(currentTaskIndex < tasks.length){
        alert(currentTask);
    } else {
        console.log("clicked");
    }
  }

  function speak(text) {
    if (synth && !isSpeaking) {
        isSpeaking = true;
      const utterance = new SpeechSynthesisUtterance(text);
        utterance.onend = () => {
            isSpeaking = false;
        }
      synth.speak(utterance);
    } else if (isSpeaking){
        synth.cancel();
        isSpeaking = false;
        const utterance = new SpeechSynthesisUtterance(text);
        utterance.onend = () => {
            isSpeaking = false;
        }
        synth.speak(utterance);
    }
      else {
      console.error("Speech synthesis is not available.");
    }
  }

  function startTimer() {
    timer = setTimeout(() => {
      if (currentTaskIndex < tasks.length) {
        nextTask();
      }
    }, 2000);
  }

  $: if (currentTaskIndex === 0 && tasks.length > 0) {
    speak(currentTask);
    startTimer();
  }
</script>

<Nav />
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Vision</Card.Title>
    <Card.Description>Do quick actions with limited vision</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Button disabled={currentTask === "All tasks completed!"} type="button" variant="outline" class="h-40 w-full">
          {currentTask}
        </Button>
        <Button on:click={handleYes} type="button" class="h-40 w-full">
          Yes
        </Button>
      </div>
    </div>
  </Card.Content>
</Card.Root>
