<template>
    <div>
        <CountryDetails :country="selectedCountry"></CountryDetails>

        <ul v-if="data" v-for="country in data" :key="country.alpha3Code">
            <router-link :to="`/list/${country.alpha3Code}`">
                <li @country-selected="countryHandler">
                    <img :src="`https://flagpedia.net/data/flags/icon/72x54/${country.alpha2Code.toLowerCase()}.png`"
                        alt='flag image' /><br>
                    {{ country.name.official }}
                </li>
            </router-link>

        </ul>
    </div>

</template>

<script>
import CountryDetails from './CountryDetails.vue'
export default {

    components: {
        CountryDetails
    },

    created() {

        let countryId = this.$route.params.alpha3Code
        if (countryId) this.selectedCountry = this.data.find(element => element.alpha3Code === countryId)

    },

    data() {
        return {
            selectedCountry: null
        }
    },
    props: {
        data: {
            type: Array,
            default: {}
        }
    },

    methods: {
        countryHandler(countryData) {

            this.selectedCountry = countryData;
        },
    },

     watch: {
            '$route.params.alpha3Code'() {
                if(this.data)
                    this.selectedCountry = this.data.find(element => element.alpha3Code === this.$route.params.alpha3Code )
            }
        }


}

</script>

<style>

</style>