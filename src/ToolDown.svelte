<script lang="ts">
import Card from "./Card.svelte";
import Modal from "./Modal.svelte";
import { fade } from 'svelte/transition';
interface Item {
    itemName: string;
    itemStock: number;
    itemPrice: number;
    itemTarget: number;
    itemSold: number;
    itemSrc: string;
    itemUnit: string;
  }

let Cards: Item[] = [{
  itemName: "Maggi",

  itemStock: 10,
  itemPrice: 10,
  itemTarget: 10,
  itemSold: 0,
  itemSrc: "https://m.media-amazon.com/images/I/71jfrTizZTL.jpg",
  itemUnit: "per packet"
}, {
  itemName: "Dummy Item",

  itemStock: 10,
  itemPrice: 1000,
  itemTarget: 10,
  itemSold: 10,
  itemSrc: "https://m.media-amazon.com/images/I/71jfrTizZTL.jpg",
  itemUnit: "per kg"
}, {
  itemName: "Dummy Item",

  itemStock: 10,
  itemPrice: 1000,
  itemTarget: 10,
  itemSold: 10,
  itemSrc: "https://m.media-amazon.com/images/I/71jfrTizZTL.jpg",
  itemUnit: "per kg"
}, {
  itemName: "Dummy Item",

  itemStock: 10,
  itemPrice: 1000,
  itemTarget: 10,
  itemSold: 10,
  itemSrc: "https://m.media-amazon.com/images/I/71jfrTizZTL.jpg",
  itemUnit: "per kg"
}];
let showModal: boolean = false;

function showMod(): void {
  showModal = true;
}

function additems(event):void {
  const newItem = {
    itemName: event.detail.itemName,
    itemStock: event.detail.itemStock,
    itemPrice: event.detail.itemPrice,
    itemTarget: event.detail.itemTarget,
    itemSold: event.detail.itemSold,
    itemSrc: event.detail.itemSrc,
    itemUnit: event.detail.itemUnit
  };

  Cards = [...Cards, newItem];
  showModal = false;
  console.log(Cards);
}

function hideModal():void {
  showModal = false;
}
</script>

<style>
.parent {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 10px;
  background-color: aqua;
}

.addNew {
  font-size: larger;
  border: 1px solid red;
  cursor: pointer;
}
</style>

<div class="parent">
    {#each Cards as Car}
    <Card itemName = {Car.itemName} itemStock = {Car.itemStock} itemPrice = {Car.itemPrice} itemTarget = {Car.itemTarget} itemSold = {Car.itemSold} itemSrc = {Car.itemSrc} itemUnit={Car.itemUnit}></Card>
    {/each}

    <button class="addNew" on:click={showMod}>Add new Item</button>
    {#if showModal}
    <div class="modal">
        <Modal on:message = {additems} on:cancel = {hideModal} ></Modal>
    </div>
    {/if}

</div>
