<script lang="ts">
	import { db } from '$lib/db';
	import { collection, getDocs } from 'firebase/firestore';

	const col = collection(db, 'vols');
	const docs = getDocs(col);
	let im: string;
	let nz: string;
	let mi: string;
	let ul: string;
	let nr: string;
</script>

{#await docs then adocs}
	{#each adocs.docs as doc}
		<p>
			{doc.data()['im']}
			{doc.data()['nz']}
			{doc.data()['mi']}
			{doc.data()['ul']}
			{doc.data()['nr']}
		</p>
	{/each}
{/await}
