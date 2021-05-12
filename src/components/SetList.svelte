<script>
    import SetDetail from './SetDetail.svelte'
    export let sets = [];

</script>

<div class="set-list">
    {#each sets as set (set.setId)}
    <SetDetail {set}/>
    {/each}
</div>

<style>

    .set-list{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }

</style>