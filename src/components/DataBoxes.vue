<template>
    <div class="grid md:grid-cols-2 gap-4 rounded ">
        <!-- Box 1-->
        <div class="shadow-md bg-slate-800 p-10 text-center rounded hover:bg-yellow-700">
            <h3 class="text-3xl text-blue-900 font-bold mb-4 text-yellow-500">Cases</h3>

            <div class="text-2xl mb-4 text-white">
                <span class="font-bold text-white">New:</span>
                {{ NumberWithComas(stats.NewConfirmed) }}
            </div>
            <div class="text-2xl mb-4 text-white">
                <span class="font-bold text-white">Total:</span>
                {{ NumberWithComas(stats.TotalConfirmed) }}
            </div>
        </div>

        <!-- Box 2-->
        <div class="shadow-md bg-slate-800 p-10 text-center rounded hover:bg-yellow-700">
            <h3 class="text-3xl text-blue-900 font-bold mb-4 text-yellow-500">Deaths</h3>

            <div class="text-2xl mb-4 text-white">
                <span class="font-bold text-white">New:</span>
                {{ NumberWithComas(stats.NewDeaths) }}
            </div>
            <div class="text-2xl mb-4 text-white">
                <span class="font-bold text-white">Total:</span>
                {{ NumberWithComas(stats.TotalDeaths) }}
            </div>
        </div>
    </div>

    <!-- Box 3-->
    <div class="shadow-md bg-slate-800 p-10 text-center rounded hover:bg-yellow-700 mt-2">
        <h3 class="text-3xl text-blue-900 font-bold mb-4 text-yellow-500">Recovered</h3>

        <div class="text-2xl mb-4 text-white">
            <span class="font-bold text-white">New:</span>
            {{ NumberWithComas(stats.NewRecovered) }}
        </div>
        <div class="text-2xl mb-4 text-white">
            <span class="font-bold text-white">Total:</span>
            {{ NumberWithComas(stats.TotalRecovered) }}
        </div>
    </div>

</template>

<script>
export default {
    name: 'DataBoxes',
    props: ['stats'],
methods: {
    NumberWithComas(x){
        return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    }
},
}
</script>
