<script lang="ts">
  import "./app.css";
  import { goto } from '$app/navigation';
  import { page } from '$app/state';
  import Friends from "../lib/assets/Friends.svelte";
  import Messages from "../lib/assets/Messages.svelte";
  import Vocals from "../lib/assets/Vocals.svelte";

  function navigateTo(path: string) {
    goto(path);
  }

  function isActive(path: string): boolean {
    return page.url.pathname === path;
  }
  
</script>

<div class="relative">

  <main>
    <slot />
  </main>

  <nav class="fixed flex items-center justify-center gap-6 bottom-0 left-0 right-0  py-2 border border-t border-border ">
    <button 
      class="flex flex-col p-2 items-center rounded-md cursor-pointer hover:bg-card {isActive('/friends') ? 'bg-muted' : ''}"
      onclick={() => navigateTo('/friends')}>
      <div>
        <Friends />
      </div>
      <div>
        Friends
      </div>
    </button>
    <button 
      class="flex flex-col p-2 items-center rounded-md cursor-pointer hover:bg-card {isActive('/messages') ? 'bg-muted' : ''}"
      onclick={() => navigateTo('/messages')}>
      <div>
        <Messages />
      </div>
      <div>
        Messages
      </div>
    </button>
    <button 
      class="flex flex-col p-2 items-center rounded-md cursor-pointer hover:bg-card {isActive('/vocals') ? 'bg-muted' : ''}"
      onclick={() => navigateTo('/vocals')}>
      <div>
        <Vocals />
      </div>
      <div>
        Vocals
      </div>
    </button>
    
    
  </nav>

</div>