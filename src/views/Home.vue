<template>
  <main v-if="!loading">
    <DataTitle :title="title" :dataDate="dateTime" />
    <CountriesData @get-country="getCountryData" :countriesInfo="countries" />
    <button class="mb-5 opacity-80 font-bold bg-yellow-500 text-white rounded-full p-2
    focus:outline-none hover:opacity-100">
    See Global Covid19 Informations
  </button>
    <DataBoxes :stats="stats" />

  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-5">Waiting for Data</div>
    <img class="w-24 m-auto"
      src="https://upload.wikimedia.org/wikipedia/commons/b/b9/Youtube_loading_symbol_1_(wobbly).gif" alt="image">
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountriesData from '@/components/CountriesData'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountriesData,
  },
  data() {
    return {
      loading: true,
      title: 'Global',
      stats: {},
      dateTime: '',
      countries: [],
      loadingImage: require('../assets/load.gif'),
    }
  },
  methods: {
    async FetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary')
      if (res) {
        const data = await res.json()
        return data
      }
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },
  },
  async created() {
    const data = await this.FetchCovidData()
    this.stats = data.Global
    this.dateTime = data.Date
    this.countries = data.Countries
    this.loading = false
  },
}
</script>
