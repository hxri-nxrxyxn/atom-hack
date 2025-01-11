<script>
  import {Route, Router, Link} from 'svelte-routing'
  import "./app.css";
  import Login from "./Login.svelte"
  import Signup from "./Signup.svelte"
  import Hero from "./Hero.svelte"
  import Collect from "./Collect.svelte"
  import Dashboard from "./Dashboard.svelte"
  import Vision from "./Vision.svelte"
  import Speech from "./Speech.svelte"
  import Motion from "./Motion.svelte"
  import Hearing from "./Hearing.svelte"
  import Parent from "./Parent.svelte"
  import Sos from "./Sos.svelte"

  import { onMount, onDestroy  } from 'svelte';
  import { App  } from '@capacitor/app';
  import { useRouter  } from 'svelte-routing';
  const router = useRouter();

  onMount(() => {
    const backButtonHandler = ({ canGoBack  }) => {
      if (canGoBack) {
        // Use pop() if using svelte-spa-router:
        pop();
        // OR, if NOT using svelte-spa-router, use browser history:
        // router.history.go(-1); // or router.history.back()

      }
      App.addListener('backButton', backButtonHandler);

      return () => {
        App.removeAllListeners(); // IMPORTANT: Remove listeners on unmount

      };

    }
  })
</script>

<Router>
  <Route path="/login" component="{Login}"/>
  <Route path="/" component="{Hero}"/>
  <Route path="/signup" component="{Signup}"/>
  <Route path="/collect" component="{Collect}"/>
  <Route path="/dashboard" component="{Dashboard}"/>
  <Route path="/vision" component="{Vision}"/>
  <Route path="/speech" component="{Speech}"/>
  <Route path="/motion" component="{Motion}"/>
  <Route path="/hearing" component="{Hearing}"/>
  <Route path="/parent" component="{Parent}"/>
  <Route path="/emergency" component="{Sos}"/>
  </Router>

  <i><img src="https://icons.veryicon.com/png/System/Windows%208/Media%20Controls%20Mute.png" width="16px"></i>

<style>
  i {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    background: white;
    border-radius: 50%;
    box-shadow: 0px 0px 5px grey;
    padding: 0.5rem;
  }
</style>
