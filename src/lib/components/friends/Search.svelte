<script lang="ts">
  let searchvalue = $state('');

  import SearchIcon from "$lib/assets/SearchIcon.svelte";

  function handleSearch() {
    console.log('Recherche pour le pseudo:', searchvalue);
  }
</script>

<div>
  <div class="relative">
    <input 
      type="text" 
      bind:value={searchvalue} 
      placeholder="Search..." 
      class="w-full border border-border bg-card rounded-md outline-none px-4 py-2 "
      onkeydown={(e) => e.key === 'Enter' && handleSearch()}
    />
    <button 
      onclick={handleSearch} 
      class="absolute flex items-center gap-1 cursor-pointer right-1 top-1/2 -translate-y-1/2 bg-primary px-4 py-1 rounded-md disabled:cursor-not-allowed"
      disabled={!searchvalue.trim()}
    >
      <SearchIcon />
      <span>Search</span>
    </button>
  </div>
  <div class="pt-4">
    Afficher la liste ici
  </div>
</div>

