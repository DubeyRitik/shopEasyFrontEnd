<script lang="ts">
  import {monthlySales, p1,p2,p3} from "./stores.js"
  import { fade, fly } from 'svelte/transition';
	let totalSales = 1000;
  monthlySales.subscribe(value=> {totalSales = value;});
  let para1:string;
  let para2:string;
  let para3:string;
  p1.subscribe(value => {para1 = value;});
  p2.subscribe(value => {para2 = value;});
  p3.subscribe(value => {para3 = value;});
  let monthlyTarget:number = 5000;
  let currDay:number = 1;
  function addone():void {
    if(currDay===30)
    currDay = 0;
    currDay++;
  }
</script>


<style>
.main {
  display: grid;
  grid-template-columns: 1fr 1fr;
  background-color: rgb(125, 209, 159);
}
.mainSecond {
  display: grid;
  grid-template-columns: 1fr 1fr;
  background-color: rgb(255, 0, 0);
}
.left {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: larger;
}
.right {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: small;
}
</style>

<div class = {currDay>=15 && totalSales <monthlyTarget/2 ? "mainSecond" : "main"}>
  <div class="left">
    <h2 in:fly="{{ y: 200, duration: 2000 }}" out:fade>{para1}</h2>
    <h2 in:fly="{{ y: 200, duration: 2000 }}" out:fade>{para2}</h2>
    <h2 in:fly="{{ y: 200, duration: 2000 }}" out:fade>{para3}</h2>
  </div>
  
  <div class="right">
    <h2 >Total Sales this month</h2>
    <h1>${totalSales}</h1>
    <h2>Monthly Target</h2>
    <h2>${monthlyTarget}</h2>
    <h2>Current Day</h2>
    <h2>{currDay}/30</h2>
    <button on:click={addone}>+</button>
  </div>

</div>