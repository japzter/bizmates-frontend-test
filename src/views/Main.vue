<template>
    <div id="main">
        <v-container>
            <v-row>
                <v-col md="5" xl="6" order-md="2">
                    <Hero/>
                </v-col>
                <v-col md="7" xl="6" order-md="1">
                    <h1>Let's Visit Japan</h1>
                    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Natus, optio adipisci et harum possimus commodi atque voluptates, aliquam earum labore eligendi pariatur tenetur distinctio delectus id excepturi necessitatibus repellat tempore! Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quis consectetur unde, consequatur esse, tempore, fugiat at quisquam repellendus ipsum quasi possimus quod culpa nulla ipsa enim delectus ab iure rem!</p>
                    <p>To view more info about the cities select a city</p>
                    <v-menu
                        open-on-hover
                        bottom
                        offset-y
                    >
                        <template v-slot:activator="{ on, attrs }">
                            <v-btn
                            color="primary"
                            v-bind="attrs"
                            v-on="on"
                            >
                            SELECT A CITY
                            </v-btn>
                        </template>

                        <v-list>
                            <v-list-item
                            v-for="(item, index) in items"
                            :key="index"
                            link
                            @click="setCity(item.title)"
                            >
                                <v-list-item-title>{{ item.title }}</v-list-item-title>
                            </v-list-item>
                        </v-list>
                    </v-menu>
                    <CityInfo :city="city"/>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script>
    import Hero from '@/components/Hero';
    import CityInfo from '@/components/CityInfo';

    export default {
        name: 'Main',
        components: {
            Hero,
            CityInfo
        },
        data() {
            return {
                items: [
                    { title: 'Tokyo' },
                    { title: 'Yokohama' },
                    { title: 'Kyoto' },
                    { title: 'Osaka' },
                    { title: 'Sapporo' },
                    { title: 'Nagoya' },
                ],
                city: 'Tokyo'
            }
        },
        methods: {
            setCity(city) {
                this.city = city
            }
        },
    }
</script>

<style lang="scss" scoped>
    #main {
        height: 100%;
        background: linear-gradient( rgba(0, 0, 0, 1), rgba(0, 0, 0, .5), rgba(0, 0, 0, .1) ), url('~@/assets/bg.jpg') no-repeat center center fixed; 
        color: #fff;
    }
</style>