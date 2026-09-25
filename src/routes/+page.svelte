<script>
    import Icon from "$lib/components/icon/icon.svelte";

    import youtubeIcon from "$lib/assets/youtube.png";
    import githubIcon from "$lib/assets/github.png";
    import penguinmodIcon from "$lib/assets/penguinmod.png";

</script>

<div class="root">
    <Icon size="256px" />
    <div class="info">
        <h1>jwklong</h1>
        <div class="socials">
            <a href="https://youtube.com/@jwklong" target="_blank">
                <img src={youtubeIcon} alt="youtube" />
            </a>
            <a href="https://github.com/jwklong" target="_blank">
                <img src={githubIcon} alt="github" />
            </a>
            <a href="https://penguinmod.com/profile?user=jwklong" target="_blank">
                <img src={penguinmodIcon} alt="penguinmod" />
            </a>
        </div>
    </div>
    <a class="source" href="https://github.com/jwklong/jwklong.dev" target="_blank">view source</a>
</div>

<style>
    .root {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        height: 100%;
        font-size: 2rem;
        font-weight: bold;
        gap: 64px;
    }

    .info {
        display: flex;
        height: 256px;
        align-items: flex-start;
        justify-content: flex-start;
        flex-direction: column;
    }

    .info h1 {
        margin: 0;
    }

    .socials {
        height: 32px;
    }

    .socials img {
        height: 32px;
        aspect-ratio: 1;
        object-fit: contain;
        transition: transform 0.1s;
    }
    .socials img:hover {
        transform: scale(1.2);
    }
    .socials img:active {
        transform: scale(0.8);
    }

    .source {
        position: absolute;
        left: 8px;
        bottom: 4px;
        font-size: 1rem;
        color: #888;
        text-decoration: none;
        font-weight: 400;
    }
</style>