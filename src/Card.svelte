<script lang="ts">
  import { monthlySales,p1,p2,p3 } from "./stores.js";
	export let itemName:string = "Dummy Item";
  export let itemStock:number = 1000;
  export let itemPrice:number = 1000;
  export let itemUnit:string = "per kg";
  export let itemTarget:number = 10;
  export let itemSold:number = 0;
  export let itemSrc:string = "https://m.media-amazon.com/images/I/71jfrTizZTL.jpg";
  function sold():void {
    if(itemStock <= 5) {
      p1.update(v => `Stock up more ${itemName}`)
    }
    if(itemStock == 0) {
      alert("cannot sell, as stock over");
      return;
    }

    itemStock--;
    itemSold++;
    monthlySales.update(n => n+itemPrice);

  }
</script>


<style>
  .normal {
    background-color: rgb(211, 198, 198);
  }
  .red{
    background-color: rgb(203, 91, 91);
  }
img {
  width: 100px;
  height: 100px;
  object-fit: cover;
}
</style>
<div class="{itemStock >= 5 ? 'normal' : 'red'}">
  <div class="image">
    <img src={itemSrc} alt="">
  </div>
  <div> 
   <h1>{itemName}</h1>
   <h3> Cost: {itemPrice} {itemUnit} </h3>
   <h3>Stock: {itemStock}</h3>
   <h3>Target units sold: {itemSold}/{itemTarget}</h3>
   <button on:click={sold}>Sold a unit</button>
  </div>
</div>