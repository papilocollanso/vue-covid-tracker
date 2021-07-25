<template>
    <div>
<div >

<!--Box 1 -->
<div class="shawdow-md bg-green-100 p-10 text-center rounded">
<h3 class="text-3xl text-green-900 font-bold font-italic mb-4">Cases</h3>
<div class="text-2xl mb-4">
<span class="font-bold font-italic">New:</span>
{{numberWithCommas(stats.NewConfirmed)}}


</div>
<div class="text-2xl mb-4">
<span class="font-bold font-italic">Total:</span>
{{numberWithCommas(stats.TotalConfirmed)}}


</div>
</div>
</div>

<h2 class="bg-white text-white">nothing</h2>

<!--Box 2 -->
<div>


<div class="shawdow-md bg-green-200 p-10 text-center rounded">
<h3 class="text-3xl text-green-900 font-bold font-italic mb-4">Deaths</h3>
<div class="text-2xl mb-4">
<span class="font-bold font-italic">New:</span>
{{numberWithCommas(stats.NewConfirmed)}}


</div>
<div class="text-2xl mb-4">
<span class="font-bold font-italic">Total:</span>
{{numberWithCommas(stats.TotalConfirmed)}}


</div>
</div>
</div>


    </div>
    
</template>

<script>
    export default {
        name:'DataBoxes',
        props:['stats'],
        methods:{
            numberWithCommas(x){
                  return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>