<script>
  import Nav from "./Nav.svelte"
  import {Router, Link} from "svelte-routing"
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";

  let value1 = $state("")
  let value2 = $state("")
  function fetchDataPeriodically1(endpoint, interval = 5000) {
    const fetchData = () => {
          fetch(endpoint)
        .then(response => {
          if (!response.ok) {
                      throw new Error(`HTTP error! status: ${response.status}`);
          }
                  return response.text(); // Or response.text() for plain text
        })
        .then(data => {
                  console.log('Data fetched:', data);
                  value1 = data;
        })
        .catch(error => {
                  value1 = "null"
        });
    };
      fetchData();
      setInterval(fetchData, interval);
  }

  function fetchDataPeriodically2(endpoint, interval = 5000) {
    const fetchData = () => {
          fetch(endpoint)
        .then(response => {
          if (!response.ok) {
                      throw new Error(`HTTP error! status: ${response.status}`);
          }
                  return response.text(); // Or response.text() for plain text
        })
        .then(data => {
                  console.log('Data fetched:', data);
                  value2 = data;
          audio.muted = false;
          audio.play().catch(error => console.error("Playback error:", error));
          
        })
        .catch(error => {
                  value2 = "nil"
                
        });
    };
      fetchData();
      setInterval(fetchData, interval);
  }

  fetchDataPeriodically1('http://192.168.90.29:5555/send-data', 100); //Different endpoint, different interval
  fetchDataPeriodically2('http://192.168.90.149:5555/send-data', 100);
  
</script>

<Nav/>
<div class="grid gap-4">

    <Card.Root class="mx-auto max-w-sm">
      <Card.Header>
        <Card.Title class="text-xl">Watch Readings</Card.Title>
        <Card.Description>Realtime readings from watch</Card.Description>
      </Card.Header>
      <Card.Content>
        <p>
          Requires your attention for {value1}
        </p>
      </Card.Content>
    </Card.Root>

    <Card.Root class="mx-auto max-w-sm">
      <Card.Header>
        <Card.Title class="text-xl">Gesture Control Readings</Card.Title>
        <Card.Description>Gesture readings</Card.Description>
      </Card.Header>
      <Card.Content>
        <p>
          {#if value2 == "Fall detected"}
            Detected possible fall. Contact the patient Immediately
          {:else}
            Our patient is safe.
          {/if}
        </p>
      </Card.Content>
    </Card.Root>

  </div>
