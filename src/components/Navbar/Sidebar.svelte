<script>
    import links from '../../constants/links';
    import { link } from "svelte-routing";
    import globalStore from '../../stores/globalStore';
    import { fly, fade } from "svelte/transition";

</script>

<div class="sidebar-container" transition:fly={{ x: -1000}}>
    <div class="sidebar" transition:fade={{ delay: 400 }}>
        <div class="sidebar-header">
            <button class="btn-close" on:click="{() => globalStore.toggleItem('sidebar', false)}">
                <i class="fas fa-window-close"></i>
            </button>
        </div>
        <img src="/assets/images/logo.svg" class="logo sidebar-logo" alt="razors logo" />
        <ul class="sidebar-links">
            {#each links as sidelink}
                <li>
                    <a href={sidelink.url} 
                        use:link 
                        on:click={() => globalStore.toggleItem('sidebar', false)}>{sidelink.text}</a>
                </li>
            {/each}
        </ul>
    </div>
</div>