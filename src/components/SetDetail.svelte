<script>
    export let set;

</script>

<div class="set">
    <h4>{set.setId}</h4>
    <div class="set-field">
        {set.name}
    </div>
    <div class="set-field">
        {set.year}
    </div>
    <img src={set.imageUrl} media="(max-width: 100px)" alt="set image">

</div>

<style>

</style>