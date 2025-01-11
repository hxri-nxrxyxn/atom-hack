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

  let mytip = "";
    import { GoogleGenerativeAI } from "@google/generative-ai"; const API_KEY = "AIzaSyCjT3qZw8I6SYEqEH1x_681_4czeQB8OIw";
  const generateAI = async () => {
    const genAI = new GoogleGenerativeAI(API_KEY);
    const model = genAI.getGenerativeModel({ model: "gemini-1.5-flash" })
    const prompt = "i am a disabled person, give me unique and random quotes everytime i call this api. please make it motivating and self-help, include inspirationational action tips. just deliver the response directly"
  try {
    const result = await model.generateContent(prompt);
    console.log(result.response.text());
    mytip = result.response.text();
  } catch (error) {
  }
  }

  generateAI()
</script>


<main transition:fade={{ duration: 600 }}>
<Nav/>

<div class="grid gap-4 py-4 px-2">
  <p>{mytip}</p>
</div>
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Personalize Your Experience</Card.Title>
    <Card.Description>Tell us what you need, and we will customize the app to assist you better</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">
      <div class="grid gap-2">
        <Link to="/vision">
          <Button type="submit" variant="outline" class="w-full">Visual Accessibility</Button>
        </Link>
        <Link to="/hearing">
          <Button type="submit" variant="outline" class="w-full">Hearing Support</Button>
        </Link>
        <Link to="/motion">
          <Button type="submit" variant="outline" class="w-full">Mobility Assistance</Button>
        </Link>
        <Link to="/speech">
          <Button type="submit" variant="outline" class="w-full">Speech Assistance</Button>
        </Link>
      </div>
    </div>
  </Card.Content>
</Card.Root>
</main>
