<script lang="ts">
	import IntField from './fields/IntField.svelte';
import Node from './Node.svelte';
</script>

<Node type="MODIFIER" name="Volume Modifier">
  <IntField name="Volume" min={0} max={100} value={50} />
</Node>
