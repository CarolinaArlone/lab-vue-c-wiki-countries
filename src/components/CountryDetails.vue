<template>
    <div v-if="country" class="col-7">
        <img v-if="country" :src="`https://flagpedia.net/data/flags/w580/${country.alpha2Code.toLowerCase()}.webp`"
            alt='flag image' width="300" /><br>
        <h1>{{ country.name.official }}</h1>
        <table class="table">
            <thead></thead>
            <tbody>
                <tr>
                    <td style="width: 50%;">Capital</td>
                    <td>{{ country.capital[0] }}</td>
                </tr>
                <tr>
                    <td>Area</td>
                    <td>

                        <sup>{{ country.area }}</sup>
                    </td>
                </tr>
                <tr>
                    <td>Borders</td>
                    <td>
                        <ul v-if="borders.length > 0" v-for="border in borders">
                            <li>{{ border }}</li>
                        </ul>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>



<script>
export default {
    data() {
        return {
            borders: this.country.borders
        }
    },
    props: {
        country: {
            type: Object,
            default: {}
        }
    }
}
</script>

<style>
.table {
    text-align: center;
}
</style>