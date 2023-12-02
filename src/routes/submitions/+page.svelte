<script lang="ts">
	import { db } from '$lib/db';
	import { AppShell } from '@skeletonlabs/skeleton';
	import { addDoc, collection } from 'firebase/firestore';
	
	let im: string;
	let nz: string;
	let mi: string;
	let ul: string;
	let nr: string;
</script>

<AppShell>
	<div class="flex justify-center w-full h-96">
		<form
			on:submit|preventDefault={async (e) => {
				await addDoc(collection(db, 'vols'), { im, nz, mi, ul, nr });
			}}
		>
			<label class="label" for="imie">Imie</label>
			<input
				class="input input-success"
				type="text"
				placeholder="Podaj Imie"
				id="imie"
				bind:value={im}
			/>
			<label class="label" for="nazwisko">Nazwisko</label>
			<input
				class="input input-success"
				type="text"
				placeholder="Podaj Nazwisko"
				id="nazwisko"
				bind:value={nz}
			/>
			<label class="label" for="adres">Zamieszkanie</label>
			<input
				class="input input-warning"
				type="text"
				placeholder="Podaj swoje miasto"
				id="adres"
				bind:value={mi}
			/>
			<input
				class="input input-warning"
				type="text"
				placeholder="Podaj swoja ulice"
				bind:value={ul}
			/>
			<input
				class="input input-warning"
				type="number"
				placeholder="Podaj numer domu"
				bind:value={nr}
			/>
			<input
				type="submit"
				class="btn variant-filled rounded-full"
				value="Przeslij formulaz "
				id="kitty"
			/>
		</form>
        <a href="./vols">Cehck vols</a>
	</div>
</AppShell>

<style>
	label,
	input {
		padding: 5px;
		margin: 5px;
	}
	label {
		font-size: 50px;
		font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
	}
</style>
