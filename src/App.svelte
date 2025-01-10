<script>
  import {Route, Router, Link} from 'svelte-routing'
  import "./app.css";
  import Login from "./Login.svelte"
  import Signup from "./Signup.svelte"
  import Hero from "./Hero.svelte"
  import Collect from "./Collect.svelte"
  import Issues from "./Issues.svelte"
  import Dashboard from "./Dashboard.svelte"
  import Vision from "./Vision.svelte"
  import Speech from "./Speech.svelte"
  import Motion from "./Motion.svelte"
  import Hearing from "./Hearing.svelte"
</script>


<Router>
  <Route path="/login" component="{Login}"/>
  <Route path="/" component="{Hero}"/>
  <Route path="/signup" component="{Signup}"/>
  <Route path="/collect" component="{Collect}"/>
  <Route path="/issues" component="{Issues}"/>
  <Route path="/dashboard" component="{Dashboard}"/>
  <Route path="/vision" component="{Vision}"/>
  <Route path="/speech" component="{Speech}"/>
  <Route path="/motion" component="{Motion}"/>
  <Route path="/hearing" component="{Hearing}"/>
</Router>


<style></style>