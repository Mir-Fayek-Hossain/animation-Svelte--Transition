<script>
	//installation command for transition
	// npm i svelte-transitions
	import { blur, fade, fly, scale, slide } from 'svelte/transition';
	let visibleViaFade = true;
	let visibleViaScale = true;
	let visibleViaBlur = true;
	let visibleViaSlide = true;
	let visibleViaFlyToX = true;
	let visibleViaFlyToY = true;
	let visibleViaIO = true;
	let multipleAnimation = true;
	let valArray = [1, 2, 3];
</script>

<!-- Fade -->
<label>
	<input type="checkbox" bind:checked={visibleViaFade} />
	visible
</label>

{#if visibleViaFade}
	<p transition:fade={{ delay: 250, duration: 300 }}>Fades in and out</p>
{/if}

<label>
	<input type="checkbox" bind:checked={visibleViaScale} />
	visible
</label>

{#if visibleViaScale}
	<p transition:scale>scale in and out</p>
{/if}

<!-- blur -->
<label>
	<input type="checkbox" bind:checked={visibleViaBlur} />
	visible
</label>

{#if visibleViaBlur}
	<p transition:blur>blur in and out</p>
{/if}

<!-- Scale -->
<label>
	<input type="checkbox" bind:checked={visibleViaSlide} />
	visible
</label>

{#if visibleViaSlide}
	<p transition:slide>slide in and out</p>
{/if}

<!-- Fly -->
<label>
	<input type="checkbox" bind:checked={visibleViaFlyToX} />
	visible
</label>

{#if visibleViaFlyToX}
	<!-- x:40 it will horizontally fly to 40px -->
	<p transition:fly={{ x: 40 }}>fly in and out</p>
{/if}

<label>
	<input type="checkbox" bind:checked={visibleViaFlyToY} />
	visible
</label>

{#if visibleViaFlyToY}
	<!-- y:40 it will verticvally fly to 40px -->
	<p transition:fly={{ y: 40 }}>fly in and out</p>
{/if}

<!-- in n out -->
<label>
	<input type="checkbox" bind:checked={visibleViaIO} />
	visible
</label>

{#if visibleViaIO}
	<!-- y:40 it will verticvally fly to 40px -->
	<p in:fly={{ x: 40 }} out:blur>in and out</p>
{/if}

<!-- Multiple animation nested -->
<label>
	<input type="checkbox" bind:checked={multipleAnimation} />
	visible
</label>
{#if multipleAnimation}
	<div transition:blur={{ duration: 400 }}>
		{#each valArray as item, index}
			<!-- we will use local when we need an animation while removing child element, if we dont then while removing parent then child transition out animation will run not the parent transition out-->
			<p in:fly={{ x: 40, delay: 400 + index * 300 }} out:slide|local>{item}</p>
		{/each}
	</div>
{/if}

<!-- When we are doind nested animation then we must use these in parent to prevent some animation problem in child
    youtube line :https://www.youtube.com/watch?v=M-LroTSC54E&list=PLoKaNN3BjQX20O5A1V5SUJ5kZWkfJX71U&index=3   
on:introend(())
on:outroend(()) -->

<!-- 
    for more cool buiild-in svelte animation
    use svelt easing 
    example on svelt doc :https://svelte.dev/examples/easing
    youtube tutorial:https://www.youtube.com/watch?v=xQc9mwBGJ5Q&list=PLoKaNN3BjQX20O5A1V5SUJ5kZWkfJX71U&index=4
 -->
