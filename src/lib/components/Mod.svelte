<script>
    export let displayName;
    export let internalName;

    export let tagline;
    export let description;
    export let creators;
    export let releaseDate;
    export let lastUpdated;
    export let version;
    export let pageUrl;
    export let sourceUrl;
    export let iconUrl;
    export let downloadUrl;
    export let game;
    export let console;
    export let consoleCompatible;
    export let recommendedEmulator;
    export let modGroup;

    export let color;

    import Img from "@zerodevx/svelte-img";
    import Icon from "svelte-awesome";
    import {
        faGithub,
    } from "@fortawesome/free-brands-svg-icons";
    import {
        faDownload,
        faFileLines,
    } from "@fortawesome/free-solid-svg-icons";
    import { faBook, faHammer, faPlay } from "@fortawesome/free-solid-svg-icons";

</script>

<div class="mod-list-item flex flex-row gap-8" style="--color: #fff">
    <div class="flex flex-col side-bar">
        <img src={iconUrl} alt="Mod Icon" class="mod-img"/>
        <div class="mod-release">{releaseDate}</div>
        <div class="mod-version">v{version}</div>
        <div class="mod-creators">{creators[0]}</div>
        <div class="mod-platform">{console} - <a href={"./games"}>{game}</a></div>
        <div class="mod-emu">{recommendedEmulator}</div>
    </div>
    <div class="flex flex-col">
        <div class="flex flex-col">
            <div class="mod-name">
                {#if pageUrl != null}<a href={pageUrl}>{displayName}</a>
                {:else} {displayName} {/if}
            </div>
            <div class="mod-tagline">{tagline}</div>
            <div class="mod-description">{description}</div>
        </div>
        <div class="flex flex-row gap-4 justify-end mod-links">
            {#if sourceUrl != null}<a href={sourceUrl}><Icon data={faGithub} scale={1.1} class="mr-1.5" /></a>{/if}
            {#if downloadUrl != null}<a href={downloadUrl}><Icon data={faDownload} scale={1.1} class="mr-1.5" /></a>{/if}
        </div>
    </div>
</div>


<style>
    .mod-list-item {
        /* If we want, we can blend in a mod-specific color, or a platform specific color, or whatever we would like */
        /* What {color} represents is controlled by the div for now */
        background-color: color-mix(in srgb, #fff 80%, var(--color));
        border-radius: 10px;
        padding: 20px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        margin-bottom: 20px;
        width: 90%;
        max-width: 500px;
    }
    .mod-list-item:hover{
        background-color: color-mix(in srgb, #fff 40%, var(--color));
        transition-duration:0.1s;
    }

    .mod-name {
        font-weight: bold;
        color: #007bff;
        margin-bottom: 2px;
        font-size:larger;
    }
    .mod-tagline {
        font-weight: bold;
        margin-bottom: 12px;
    }

    .mod-name a {
        text-decoration: none;
        color: inherit;
    }

    .mod-description {
        color: #666;
        max-width:320px;
        height:180px;
        white-space: pre-line;
    }

    .mod-img{
        width:64px;
        height:64px;
    }

    .mod-links{
        margin-top:auto;
        width:320px;
    }

    .side-bar{
        width:96px;
        height:270px;
        box-sizing:border-box;
    }
    .mod-creators{
        width:96px;
        text-wrap:wrap;
        overflow-wrap:break-word;
    }
</style>