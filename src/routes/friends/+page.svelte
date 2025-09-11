<script lang="ts">
  import Search from '$lib/components/friends/Search.svelte';
  import AllFriends from '$lib/components/friends/AllFriends.svelte';
  import FriendRequests from '$lib/components/friends/FriendRequests.svelte';


  let activeComponent = 'Search';

  function setActiveComponent(component: string) {
    activeComponent = component;
  }
</script>

<div class="flex h-full pt-6">
  <aside class="h-full w-50 flex flex-col gap-1 px-4">
    <button 
      class="cursor-pointer flex w-full text-start rounded-md px-2 py-1 hover:bg-card"
      onclick={() => setActiveComponent('Search')}
    >
      <span>Search</span>
    </button>
    <button 
      class="cursor-pointer flex justify-between w-full text-start rounded-md px-2 py-1 hover:bg-card"
      onclick={() => setActiveComponent('AllFriends')}
    >
      <span>All friends</span>
      <span>20</span>
    </button>
    <button 
      class="cursor-pointer flex justify-between w-full text-start rounded-md px-2 py-1 hover:bg-card"
      onclick={() => setActiveComponent('FriendRequests')}
    >
      <span>Friend requests</span>
      <span>6</span>
    </button>
  </aside>

  <div class="flex-1 px-4">
    {#if activeComponent === 'Search'}
      <Search />
    {:else if activeComponent === 'AllFriends'}
      <AllFriends />
    {:else if activeComponent === 'FriendRequests'}
      <FriendRequests />
    {/if}
  </div>

</div>
