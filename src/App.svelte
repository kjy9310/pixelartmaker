<script>
	export let name;
	const width = 30
	document.documentElement.style.setProperty('--width', width)
	const height = 30
	document.documentElement.style.setProperty('--height', height)
	const initArray = () =>{
		return (new Array(width)).map(()=>{
			return new Array(height)
		})
	}
	let pixelCanvas = initArray()
/*
	let size = 100
	let step = 1
	
	$: document.documentElement.style.setProperty('--size', size + 'px')
	
	setInterval(() => {
		size += step
		
		if (size > 300 || size < 100) {
		step *= -1
		}
	}, 17)
*/
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<p>added extra</p>
	
	{#each pixelCanvas as row, x}
		{#each row as _, y}
			<span>{x}-{y}</span>
		{/each}
	{/each}

	<div id="box">
        <div id="pixel">
        </div>
    </div>
    <input type="color" id="color"/>
    <table id="table">
    
	</table>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	#table {
        margin-top:200px
    }
    #table div {
        border: 1px solid grey;
    }
    .wrap {
        position: relative;
    }
    #box {
        position: relative;
        width: 30px;
        height: 30px;
        overflow: hidden;
        transform: scale(2,2)
    }
    #pixel {
        position: absolute;
        width: var(--width)px;
        height: var(--height)px;
        clip-path: inset(0px calc(-1*var(--width))px calc(-1*var(--height)px) 0px);
        margin-left: calc(-1*var(--width))px;
        margin-top: calc(-1*var(--height)px);
    }
</style>