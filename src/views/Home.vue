<template>
<div class="mx-auto justify-center align-center">
 <main  class="home font-style: italic" v-if="!loading">
  <DataTitle v-bind:text="title" :dataDate="dataDate"/>
  <DataBoxes v-bind:stats="stats"/>
  <CountrySelect @get-country="getCountryData" v-bind:countries="countries"/>
  <button 
  @click="clearCountryData"
  
   v-if="stats.Country " class="bg-green-800 text-white rounded p-3 mt-10 focus:outline-none hover:bg-red-600">
  Clear Country</button>
    
  </main>

  <main  class="flex flex-col align-center justify-center text-center" v-else>
  <div class="text-gray-500 text-3xl mt-10 mb-6">

Fetching Data
  </div>
  <img :src="loadingImage" class="w-24 m-auto" alt="Loading Image"/>
  
  </main>
</div>
 

</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  components: {
    DataTitle, 
    DataBoxes,
    CountrySelect,
    },
    data(){
      return{
        loading:true,
        title:'Global',
        dataDate:'',
        status:{},
        countries:[],
        loadingImage:require('../assets/loading.jpg')
      };
    
  },
  methods:{
    async fetchCovidData(){
      const res=await fetch('https://api.covid19api.com/summary');
      const data=await res.json();
      return data;

    },
    getCountryData(country){
this.stats=country
this.title=country.Country
    },
    async clearCountryData(){

this.loading = true
const data= await this.fetchCovidData()
this.title='Global'
this.stats=data.Global
this.loading=false
    },
  },
  async created () {
const data= await this.fetchCovidData()
this.dataDate=data.Date;
this.stats=data.Global;
this.countries=data.Countries
this.loading=false;
  },
}
</script>
