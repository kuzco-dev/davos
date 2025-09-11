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

<div class="h-screen flex flex-col">
  <main class="flex-1">
    <slot />
  </main>

  <nav class="flex items-center justify-center gap-6 w-full  h-20 border border-t border-border ">
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
    <button 
      class="flex flex-col p-2 items-center rounded-md cursor-pointer hover:bg-card {isActive('/settings') ? 'bg-muted' : ''}"
      onclick={() => navigateTo('/settings')}>
      <div>
        SE
      </div>
      <div>
        Settings
      </div>
    </button>
    
    
  </nav>

</div>