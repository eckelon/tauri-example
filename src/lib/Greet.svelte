<script>
  import { invoke } from "@tauri-apps/api/tauri";
  let name = "";
  let greetMsg = "";

  async function greet_on_key({ key }) {
    if (key !== 'Enter') {
      return;
    }

    greetMsg = await invoke("greet", { name });
  }

  async function greet() {
    // Learn more about Tauri commands at https://tauri.app/v1/guides/features/command
    greetMsg = await invoke("greet", { name });
  }
</script>

<div>
  <div class="row">
    <input id="greet-input" placeholder="Enter a name..." bind:value={name}  on:keypress={greet_on_key}/>
    <button on:click={greet} > Greet </button>
  </div>
  <p>{greetMsg}</p>
</div>
