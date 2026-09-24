<script>
    import { onMount } from 'svelte';
    import bgIcon from './bg.svg';
    import fgIcon from './fg.svg';

    let {
        size = "0px"
    } = $props();

    /** @type {HTMLImageElement} */
    let fgElement;
    onMount(() => {
        let listener = e => {
            let cx = fgElement.x + fgElement.width / 2;
            let cy = fgElement.y + fgElement.height / 2;

            let dx = (e.clientX - cx) / fgElement.width;
            dx = dx / Math.sqrt(Math.abs(dx)) || 0;
            let dy = (e.clientY - cy) / fgElement.height;
            dy = dy / Math.sqrt(Math.abs(dy)) || 0;

            fgElement.style.transform = `rotateY(${dx*15}deg) rotateX(${dy*15}deg)`
        }

        addEventListener('mousemove', listener);
        return () => removeEventListener('mousemove', listener)
    })
</script>

<div style:height={size}>
    <img src={bgIcon} alt="" />
    <img bind:this={fgElement} src={fgIcon} class="fg" alt="" />
</div>

<style>
    div {
        aspect-ratio: 1;
        position: relative;
        overflow: hidden;
        border-radius: 10%;
    }
    
    img {
        position: absolute;
    }
</style>