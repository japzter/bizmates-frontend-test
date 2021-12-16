<template>
    <v-card
    :loading="loading"
    class="mx-auto my-12"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-card-title>{{ myCity }} Weather Forecast</v-card-title>

    <v-card-text>
        <Weather :forecasts="forecasts"/>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-title>Venues</v-card-title>
     <v-list-item v-for="(venue, i) in venues" :key="i">
      <v-list-item-content>
        <v-list-item-title v-html="venue.name"></v-list-item-title>
      </v-list-item-content>
    </v-list-item>
  </v-card>
</template>

<script>
    import Weather from '@/components/Weather'
    import axios from 'axios'

    export default {
        props: ['city'],
        components: {
            Weather,
        },
        data: () => ({
            loading: false,
            myCity: 'Tokyo',
            venues: [],
            forecasts: []
        }),
        created () {
            this.getData();
        },
        methods: {
            async getData() {
                this.loading = true;
                await Promise.all([
                    this.fetchWeather(), 
                    this.fetchVenue(),
                ])
                this.loading = false;
            },
            async fetchWeather() {
                let { data } = await axios.get(`http://127.0.0.1:8000/api/weather/${this.city}`)
                
                if (data) {
                    this.forecasts = data.list
                }
            },
            async fetchVenue() {
                let { data } = await axios.get(`http://127.0.0.1:8000/api/venue/search/${this.city}`)
                if (data) {
                    this.venues = data.response.venues;
                }
            }
        },

        watch: {
            city(newValue) {
                this.getData();
                this.myCity = newValue;
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>