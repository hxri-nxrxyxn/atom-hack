
<script>
  import Nav from "./Nav.svelte";
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import { Link, Router } from "svelte-routing"
  import * as Table from "$lib/components/ui/table";
  const randomBetween = (min, max) => Math.trunc(Math.random() * (max - min + 1)) + min; 
  let myval = randomBetween(93.00, 94.00)
</script>

<Nav />
<Card.Root class="mx-auto max-w-sm">
  <Card.Header>
    <Card.Title class="text-xl">Visual Assistance</Card.Title>
    <Card.Description>See the world differently with smart tools that guide and read for you!</Card.Description>
  </Card.Header>
  <Card.Content>
    <div class="grid gap-4">

      <div class="grid gap-2">
        <Button type="button" variant="outline" class="h-40 w-full">
          <h1>Calling Emergency Services</h1>
        </Button>
      </div>

      <div class="grid gap-2">
        <Link to="/">
          <Button type="button" class="h-40 w-full">
            Cancel
          </Button>
        </Link>
      </div>

      <div class="grid gap-2">
        <Table.Root>
          <Table.Caption>A list of your recent invoices.</Table.Caption>
          <Table.Header>
            <Table.Row>
              <Table.Head class="w-[100px]">Vitals</Table.Head>
              <Table.Head>Readings</Table.Head>
            </Table.Row>
          </Table.Header>
          <Table.Body>
            <Table.Row>
              <Table.Cell class="font-medium">Heart Rate</Table.Cell>
              <Table.Cell>68bpm</Table.Cell>
            </Table.Row>
            <Table.Row>
              <Table.Cell class="font-medium">Blood Pressure</Table.Cell>
              <Table.Cell>120/89mmHg</Table.Cell>
            </Table.Row>
            <Table.Row>
              <Table.Cell class="font-medium">SpO2</Table.Cell>
              <Table.Cell>{myval}</Table.Cell>
            </Table.Row>
            <Table.Row>
              <Table.Cell class="font-medium">Age</Table.Cell>
              <Table.Cell>20</Table.Cell>
            </Table.Row>
            <Table.Row>
              <Table.Cell class="font-medium">Height</Table.Cell>
              <Table.Cell>193cm</Table.Cell>
            </Table.Row>
            <Table.Row>
              <Table.Cell class="font-medium">Weight</Table.Cell>
              <Table.Cell>58kg</Table.Cell>
            </Table.Row>
            <Table.Row>
              <Table.Cell class="font-medium">Allergy</Table.Cell>
              <Table.Cell>Dust</Table.Cell>
            </Table.Row>
            <Table.Row>
              <Table.Cell class="font-medium">Medication</Table.Cell>
              <Table.Cell>None</Table.Cell>
            </Table.Row>
          </Table.Body>
        </Table.Root>
      </div>
    </div>
  </Card.Content>
</Card.Root>
