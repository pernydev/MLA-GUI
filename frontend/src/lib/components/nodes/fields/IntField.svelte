<script lang="ts">
	let { value, name, min, max }: { value: number; name: string; min: number; max: number } =
		$props();

	let previousX: number = 0;
	let isDragging: boolean = false;
	const SENSITIVITY = 0.45;

	function onmousedown(event: MouseEvent) {
		previousX = event.clientX;
		isDragging = true;
	}

	function clamp(value: number, min: number, max: number): number {
		return Math.min(Math.max(value, min), max);
	}

	function onmousemove(event: MouseEvent) {
		if (!isDragging) return;

		// Calculate the delta movement
		const deltaX = event.clientX - previousX;
		const newValue = Math.round(value + deltaX * SENSITIVITY);
		value = clamp(newValue, min, max);

		previousX = event.clientX;
	}

	function onmouseup() {
		previousX = 0;
		isDragging = false;
	}

	$effect(() => {
		if (!value) {
			value = min;
		}

		if (value < min) {
			value = min;
		} else if (value > max) {
			value = max;
		}

		if (value % 1 !== 0) {
			value = Math.round(value);
		}
	});
</script>

<svelte:body on:mousemove={onmousemove} on:mouseup={onmouseup} />

<div class="flex gap-4 items-center">
	<span class="font-mono uppercase text-sm">{name}</span>
	<div class="bg-border rounded-sm p-1 pl-4 flex-1 cursor-ew-resize relative z-0" {onmousedown}>
		<span
			class="absolute top-0 left-0 bottom-0 bg-primary/20 rounded-sm z-[-1]"
			style={`width: ${((value - min) / (max - min)) * 100}%`}
		/>
		<input
			type="number"
			bind:value
			class="font-mono text-xs w-fit"
			{min}
			{max}
			{oninput}
		/>
	</div>
</div>

<style>
	input {
		background: transparent;
		border: transparent;
	}

	input::-webkit-outer-spin-button,
	input::-webkit-inner-spin-button {
		-webkit-appearance: none;
		margin: 0;
	}

	/* Firefox */
	input {
		-moz-appearance: textfield;
	}

	input:focus {
		outline: none;
	}
</style>
