<script lang="ts">
import {
  createEventDispatcher
} from 'svelte';
const dispatch = createEventDispatcher();
let itemName:string;
let itemPrice:number;
let itemSold:number = 0;
let itemSrc:string;
let itemStock:string;
let itemUnit:string;
let itemTarget:number;
function additem():void {
  const data = {itemName,itemPrice,itemSold,itemSrc,itemStock,itemUnit,itemTarget};
  dispatch('message', data);

}


function cancel():void {
  dispatch('cancel', {
    'text': 'cancel'
  });
}
</script>

<style>

</style>

<div>
    <h1>Name:</h1>
    <input type="text" bind:value={itemName}>
    <h1>Unit</h1>
    <input type="text" bind:value={itemUnit}>
    <h1>Price per unit</h1>
    <input type="number" bind:value={itemPrice} >
    <h1>Monthly Target to sell</h1>
    <input type="number" bind:value={itemTarget}>
    <h1>Stock:</h1>
    <input type="number" bind:value={itemStock}>
    <h1>Image URL</h1>
    <input type="text" bind:value={itemSrc}>
    <button on:click={additem}>Add item</button>
    <button on:click={cancel}>Cancel</button>
</div>
