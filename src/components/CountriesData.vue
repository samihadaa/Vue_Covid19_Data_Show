<template>
<select @change="onChange"
v-model="selected"
class="form-select mx-auto mt-10 mb-10 block w-1/4 border border-amber-500 p-3 rounded">
    <option class=" font-bold " value="0" selected="selected">Select Your Country</option>
    <option class="" v-for="country in countriesInfo" :key="country.ID" :value="country.ID">{{ country.Country }}</option>
</select>
</template>

<script>
export default {
    name: 'CountriesData',
    props: ['countriesInfo'],
data(){
    return {
        selected: 0,
    }
},
methods: {
    onChange(){
        const country = this.countriesInfo.find((element) => element.ID === this.selected )
        this.$emit('get-country', country)
    }
}
}
</script>

