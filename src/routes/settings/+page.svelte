<script lang="ts">

  import Profile from "$lib/components/settings/Profile.svelte";
  import Voice from "$lib/components/settings/Voice.svelte";

  let activeComponent = 'Profile';

  function setActiveComponent(component: string) {
    activeComponent = component;
  }
</script>

<div class="flex h-full pt-6">
  <aside class="h-full w-50 flex flex-col gap-1 px-4">
    <button 
      class="cursor-pointer flex w-full text-start rounded-md px-2 py-1 hover:bg-card"
      onclick={() => setActiveComponent('Profile')}
    >
      <span>Profile</span>
    </button>
    <button 
      class="cursor-pointer flex justify-between w-full text-start rounded-md px-2 py-1 hover:bg-card"
      onclick={() => setActiveComponent('Voice')}
    >
      <span>Voice</span>
    </button>
  </aside>

  <div class="flex-1 px-4">
    {#if activeComponent === 'Profile'}
      <Profile />
    {:else if activeComponent === 'Voice'}
      <Voice />
    {/if}
  </div>
</div>