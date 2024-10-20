<script>
	import '../styles.css/';
	let source = $state('');
	let capitalised = $derived(source.toUpperCase());

	let letters = $derived(capitalised.split(''));
	let code = $derived(
		letters
			.map((char) => morse?.[char] || '|')
			.join('')
			.split('|')
	);

	const dash = '---';
	const dot = '';

	let morse = {
		A: [dot, dash],
		B: [dash, dot, dot, dot],
		C: [dash, dot, dash, dot],
		D: [dash, dot, dot],
		E: [dot],
		F: [dot, dot, dash, dot],
		G: [dash, dash, dot],
		H: [dot, dot, dot, dot],
		I: [dot, dot],
		J: [dot, dash, dash, dash],
		K: [dash, dot, dash],
		L: [dot, dash, dot, dot],
		M: [dash, dash],
		N: [dash, dot],
		O: [dash, dash, dash],
		P: [dot, dash, dash, dot],
		Q: [dash, dash, dot, dot],
		R: [dot, dash, dot],
		S: [dot, dot, dot],
		T: [dot],
		U: [dot, dot, dash],
		V: [dot, dot, dot, dash],
		W: [dot, dot, dash],
		X: [dash, dot, dot, dash],
		Y: [dash, dot, dash, dash],
		Z: [dash, dash, dot, dot]
	};
	Object.entries(morse).forEach(([key, codeArray]) => {
		morse[key] = codeArray.join('');
	});
</script>

<input bind:value={source} type="text" />
{code}

<!-- {#each code as word}
	<span class="word">{word}</span>
{/each} -->

<!-- <div class="output">{code}</div> -->
<style>
	.word {
		padding: 0.125em;
		margin: 0 0.125em;
		background-color: white;
	}
</style>
