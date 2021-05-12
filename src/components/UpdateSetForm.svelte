<script>
    import { createEventDispatcher } from 'svelte';
    import Button from '../shared/Button.svelte'

    let dispatch =  createEventDispatcher ();

    let fields = { setId: '', name: '', year:'', numParts:'', status:'', price:'', uvp:''}
    let error = { setId: '', name: '', year:'', numParts:'', status:'', price:'', uvp:''}
    let valid = false;

    const handleSubmit = () =>{
        valid = true;

        if(valid){
            let set = {...fields}
            dispatch('add', set);
        }

        
    }

</script>


<form on:submit|preventDefault={handleSubmit}>
    <div class="form-field">
        <label for="setid">Set Id:</label>
        <input type="text" id="setId" bind:value={fields.setId}>    
    </div>
    <div class="form-field">
    <label for="name">Name</label>
    <input type="text" id="name"  bind:value={fields.name}>
</div>
    <div class="form-field">
    <label for="year">Year</label>
    <input type="text" id="year" bind:value={fields.year}>
    <div class="form-field">
    <label for="numParts">No. Parts</label>
    <input type="text" id="numParts" bind:value={fields.numParts}>
</div>
    <div class="form-field">
    <label for="status">Status</label>
    <input type="text" id="status" bind:value={fields.status}>
</div>
    <div class="form-field">
    <label for="price">Price</label>
    <input type="text" id="price" bind:value={fields.price}>
</div>
    <div class="form-field">
    <label for="priceUvp">UVP</label>
    <input type="text" id="priceUvp" bind:value={fields.uvp}>
</div>
    <Button type="secondary" flat={true}>Add Set</Button>
</form>

<style>
    form{
        width: 400px;
        margin: 0 auto;
        text-align: center;
    }
    .form-field{
        margin: 18px auto;
    }
    input{
        width: 100%;
        border-radius: 6px;

    }label{
        margin: 10px auto;
        text-align: left;
    }
</style>