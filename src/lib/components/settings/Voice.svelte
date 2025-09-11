<script>
  import { onMount } from 'svelte';
  
  let inputDevices = [];
  let outputDevices = [];
  let selectedInputDevice = '';
  let selectedOutputDevice = '';
  let isLoading = true;

  async function getAudioDevices() {
    try {
      // Demander les permissions pour accéder aux périphériques
      await navigator.mediaDevices.getUserMedia({ audio: true });
      
      // Obtenir la liste des périphériques
      const devices = await navigator.mediaDevices.enumerateDevices();
      
      // Filtrer les périphériques audio
      inputDevices = devices.filter(device => device.kind === 'audioinput');
      outputDevices = devices.filter(device => device.kind === 'audiooutput');
      
      // Sélectionner les premiers périphériques par défaut
      if (inputDevices.length > 0) {
        selectedInputDevice = inputDevices[0].deviceId;
      }
      if (outputDevices.length > 0) {
        selectedOutputDevice = outputDevices[0].deviceId;
      }
      
      isLoading = false;
    } catch (error) {
      console.error('Erreur lors de l\'accès aux périphériques audio:', error);
      isLoading = false;
    }
  }

  onMount(() => {
    getAudioDevices();
  });
</script>

<div class="flex flex-col gap-6">
  <div class="flex flex-col">
    <h2 class="pb-1 border-b border-border">
      Input peripheral 
    </h2>
    <div class="mt-4">
      {#if isLoading}
        <div class="p-3 text-center text-muted-foreground bg-muted rounded-md">
          Chargement des périphériques...
        </div>
      {:else if inputDevices.length === 0}
        <div class="p-3 text-center text-muted-foreground bg-muted rounded-md border border-dashed">
          Aucun périphérique d'entrée détecté
        </div>
      {:else}
        <select 
          bind:value={selectedInputDevice}
          class="w-full p-2 border border-border rounded-md bg-background text-foreground focus:outline-none focus:ring-2 focus:ring-primary"
        >
          {#each inputDevices as device}
            <option value={device.deviceId}>
              {device.label || `Microphone ${device.deviceId.slice(0, 8)}...`}
            </option>
          {/each}
        </select>
      {/if}
    </div>
  </div>
  <div class="flex flex-col">
    <h2 class="pb-1 border-b border-border">
      Output peripheral 
    </h2>
    <div class="mt-4">
      {#if isLoading}
        <div class="p-3 text-center text-muted-foreground bg-muted rounded-md">
          Chargement des périphériques...
        </div>
      {:else if outputDevices.length === 0}
        <div class="p-3 text-center text-muted-foreground bg-muted rounded-md border border-dashed">
          Aucun périphérique de sortie détecté
        </div>
      {:else}
        <select 
          bind:value={selectedOutputDevice}
          class="w-full p-2 border border-border rounded-md bg-background text-foreground focus:outline-none focus:ring-2 focus:ring-primary"
        >
          {#each outputDevices as device}
            <option value={device.deviceId}>
              {device.label || `Haut-parleur ${device.deviceId.slice(0, 8)}...`}
            </option>
          {/each}
        </select>
      {/if}
    </div>
  </div>
</div>