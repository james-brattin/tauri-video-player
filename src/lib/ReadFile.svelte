<script lang="ts">
	// import { invoke } from '@tauri-apps/api/tauri';
	// import { onMount } from 'svelte';
	// import { writable } from 'svelte/store';

	// onMount(async () => {
	//     const content = await invoke('read_file', { path: 'src/lib/ReadFile.svelte' });
	//     fileContent.set(content);
	// });

	import { open } from '@tauri-apps/api/dialog';
	import { BaseDirectory, readTextFile } from '@tauri-apps/api/fs';
	import { basename, documentDir } from '@tauri-apps/api/path';
	import { invoke } from '@tauri-apps/api';

	export let fileContent = '';
	const readFileContents = async () => {
		const content = await invoke('read_codefile');
		fileContent = content as string;
		// fileContent.set(content as string);
	};
	// const readFileContents = async () => {
	// 	try {
	// 		const result = await open({
	// 			multiple: false,
	// 			directory: false,
	// 			defaultPath: await documentDir()
	// 		});
	// 		if (result) {
	// 			console.log(result);
	// 			const base = await basename(result as string);
	// 			const content = await readTextFile(base, { dir: BaseDirectory.Document });
	// 			console.log(content);
	// 		}
	// 	} catch (error) {
	// 		console.log(error);
	// 	}
	// };
</script>

<div>
	<button on:click={readFileContents}>Open file explorer</button>
	{fileContent}
</div>
