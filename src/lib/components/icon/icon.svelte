<script>
    import { onMount } from 'svelte';
    import bgIcon from './bg.svg';
    import fgFrontIcon from './fg-front.svg';
    import fgBackIcon from './fg-back.svg';

    let {
        size = "0px"
    } = $props();

    /** @type {HTMLDivElement} */ let fgElement;
    /** @type {HTMLImageElement} */ let fgFrontElement;
    /** @type {HTMLImageElement} */ let fgBackElement;
    onMount(() => {
        let listener = e => {
            let rect = fgElement.getBoundingClientRect();

            let cx = rect.x + rect.width / 2;
            let cy = rect.y + rect.height / 2;

            let dx = (e.clientX - cx) / rect.width;
            dx = dx / Math.sqrt(Math.abs(dx)) || 0;
            let dy = (e.clientY - cy) / rect.height;
            dy = dy / Math.sqrt(Math.abs(dy)) || 0;

            fgFrontElement.style.transform = `rotateY(${dx*15}deg) rotateX(${-dy*15}deg) translateZ(calc(${size} / 64))`;
            fgBackElement.style.transform = `rotateY(${dx*15}deg) rotateX(${-dy*15}deg) translateZ(calc(${size} / -64))`;
        }

        addEventListener('mousemove', listener);
        return () => removeEventListener('mousemove', listener)
    })
</script>

<div class="root" style:height={size}>
    <img src={bgIcon} alt="" />
    <div bind:this={fgElement}>
        <img bind:this={fgBackElement} src={fgBackIcon} alt="" />
        <img bind:this={fgFrontElement} src={fgFrontIcon} alt="" />
    </div>
</div>

<style>
    .root {
        aspect-ratio: 1;
        position: relative;
        overflow: hidden;
        border-radius: 10%;
    }
    
    .root * {
        position: absolute;
        height: 100%;
        aspect-ratio: 1;
    }
</style>