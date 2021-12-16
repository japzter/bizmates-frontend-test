<template>
    <v-slide-group
      show-arrows
    >
      <v-slide-item
        v-for="(forecast, n) in forecasts"
        :key="n"
      >
        <v-card
          class="ma-2 primary"
          height="125"
          width="100"
        >   
            <v-img 
                :src="`http://openweathermap.org/img/wn/${forecast.weather[0].icon}@2x.png`"
                height="75px"
            ></v-img>
            <v-card-subtitle class="mt-0 py-0 pl-2" style="color:#fff">{{ forecast.main.temp }} °F</v-card-subtitle>
            <small class="pl-2" style="color:#fff">{{ formatDate(forecast.dt) }} - {{ formatTime(forecast.dt) }}</small>
        </v-card>
      </v-slide-item>
    </v-slide-group>
</template>

<script>
    import * as moment from 'moment';

    export default {
        props: ['forecasts'],
        methods: {
            formatDate(dt) {
                return moment.unix(dt).format('MMM D');
            },
            formatTime(dt) {
                return moment.unix(dt).format('h:mm a');
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>