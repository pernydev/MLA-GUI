<script lang="ts">
	import * as Menubar from '$lib/components/ui/menubar/index.js';
	import Minus from 'lucide-svelte/icons/minus';
	import Square from 'lucide-svelte/icons/square';
	import X from 'lucide-svelte/icons/x';
	import Button from './ui/button/button.svelte';
	import * as HoverCard from './ui/hover-card';
	import Profile from './Profile.svelte';
</script>

<div class="p-4 flex gap-4" style="--wails-draggable:drag">
	<Menubar.Root class="flex-1">
		<Menubar.Menu>
			<Menubar.Trigger>File</Menubar.Trigger>
			<Menubar.Content>
				<Menubar.Item>Create Profile</Menubar.Item>
				<Menubar.Item>Import Profile</Menubar.Item>
				<Menubar.Item>Manage Profiles</Menubar.Item>
				<Menubar.Item>Export Profile</Menubar.Item>
				<Menubar.Separator />
				<Menubar.Item>Preferences</Menubar.Item>
				<Menubar.Item>Exit</Menubar.Item>
			</Menubar.Content>
		</Menubar.Menu>
		<Menubar.Menu>
			<Menubar.Trigger>Edit</Menubar.Trigger>
			<Menubar.Content>
				<Menubar.Item>Undo</Menubar.Item>
				<Menubar.Item>Redo</Menubar.Item>
				<Menubar.Separator />
				<Menubar.Item>New Virtual Device</Menubar.Item>
				<Menubar.Sub>
					<Menubar.SubTrigger>New Modifier Node</Menubar.SubTrigger>
					<Menubar.SubContent>
						<Menubar.Item>New Volume Modifier</Menubar.Item>
                        <Menubar.Item>New EQ Modifier</Menubar.Item>
					</Menubar.SubContent>
				</Menubar.Sub>
			</Menubar.Content>
		</Menubar.Menu>
	</Menubar.Root>

	<Profile />

	<HoverCard.Root>
		<HoverCard.Trigger>
			<div
				class="bg-background flex h-10 items-center justify-center space-x-1 min-w-32 rounded-md border p-1 px-4 transition-all hover:bg-green-950 hover:border-green-800"
			>
				<span class="bg-green-500 h-4 w-4 rounded-full"></span>
				<span class="text-green-500">Active</span>
			</div>
		</HoverCard.Trigger>
		<HoverCard.Content>
			<p>
				MLA GUI is currently fully active and <i>should</i> be working as expected.
			</p>
		</HoverCard.Content>
	</HoverCard.Root>

	<div
		class="bg-background flex h-10 items-center justify-center space-x-1 min-w-32 rounded-md border p-1 px-0"
	>
		<Button size="icon" variant="ghost">
			<Minus size="24" />
		</Button>

		<Button size="icon" variant="ghost">
			<Square size="24" />
		</Button>

		<Button size="icon" variant="ghost">
			<X size="24" />
		</Button>
	</div>
</div>
