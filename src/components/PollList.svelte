<script>
    // import { onDestroy, onMount } from "svelte";
    import { fade, slide, scale } from "svelte/transition";
    import { flip } from "svelte/animate";
    import PollStore from "../store/pollStore";
    import PollDetails  from "./PollDetails.svelte";
    // export let polls = []

    // const unsub = PollStore.subscribe(data => {
    //     polls = data;
    // });

    // onDestroy(() => {
    //     unsub()
    // })
</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id) }
    <div in:fade out:scale|local animate:flip={{duration: 500}}>
        <PollDetails {poll}/>
    </div>
    {/each}
</div>

<style>
    .poll-list{
        display: grid;
        grid-template-columns: 1fr 1fr;
        column-gap: 20px;
    }
</style>