<script lang="ts">
    let { children, type, name }: { children: () => any; type: string; name: string } = $props();
</script>

<div class="min-w-[200px] rounded-md border block p-4 relative">
    <span class="font-mono text-xs">{type}</span>
    <h2 class="text-lg font-bold">{name}</h2>
    
    {@render children()}
</div>