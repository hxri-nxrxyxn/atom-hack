<script>
  import {Route, Router} from 'svelte-routing'
  import "./app.css";
  import Login from "./Login.svelte"
  import Signup from "./Signup.svelte"
  import Hero from "./Hero.svelte"
  import Collect from "./Collect.svelte"
  import Issues from "./Issues.svelte"
  import Dashboard from "./Dashboard.svelte"
</script>


<Router>
  <Route path="/login" component="{Login}"/>
  <Route path="/hero" component="{Hero}"/>
  <Route path="/signup" component="{Signup}"/>
  <Route path="/collect" component="{Collect}"/>
  <Route path="/issues" component="{Issues}"/>
  <Route path="/dashboard" component="{Dashboard}"/>
</Router>


<style></style>
