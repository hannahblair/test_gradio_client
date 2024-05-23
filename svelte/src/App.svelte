<script>
  import { onMount } from "svelte";
  import { Client } from "@gradio/client";

  const hf_token = "hf_123";

  let public_app;
  let private_app;
  let private_app_with_auth;
  let endpoints;

  onMount(async () => {
    public_app = await Client.connect("hmb/hello_world");

    private_app = await Client.connect("hmb/hello_world", {
      hf_token: hf_token,
    });

    private_app_with_auth = await Client.connect("hmb/hello_world", {
      hf_token: hf_token,
      auth: ["admin", "pass123"],
    });

    endpoints = public_app.view_api();
  });
</script>

<main><h1>test</h1></main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
  }
</style>
