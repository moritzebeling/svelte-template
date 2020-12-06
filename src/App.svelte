<script>
  import { Router, Link, Route } from "svelte-routing";

  import Header from "./components/Header.svelte";
  import Footer from "./components/Footer.svelte";

  import Start from "./routes/start/Index.svelte";

  export let url = "";
</script>

<Router url="{url}">

	<div class="header">
        <div class="wrapper">
            <Header />
        </div>
    </div>

    <div class="page">
        <div class="wrapper">

            <main>
                <Route path="/"><Start /></Route>
            </main>

            <Footer />

        </div>
    </div>

</Router>

<style lang="scss">

</style>
