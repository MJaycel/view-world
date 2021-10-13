<template>
  <div>
      <!-- <div v-for="country in countries" :key="country.tld">
          <h3> {{country.name.official}} </h3>
      </div> -->

    <b-card-group columns>
            <b-card
                v-for="country in countries" 
                :key="country.tld"
                :img-src="country.flags.png"
                :img-alt="country.name.official" 
            >
                <b-card-text>
                    <h3> {{country.name.official}} </h3>
                </b-card-text>
            </b-card>
        </b-card-group > 
    </div>
</template>

<script>

import axios from 'axios'

const REST_URL = "https://restcountries.com/v3.1/all";

    export default{
        name: 'GiphyViewer',
        data(){
            return{
                countries:[],
                term: ""            
            };
        },
        mounted() {
            axios.get(`${REST_URL}`)
            .then((response) => {
                console.log(response.data)
                this.countries = response.data
                console.log(this.countries)
            })
            .catch(error => console.log(error))

            // this.term = ""
        },
        methods:{

        }
    }

</script>

<style>
@media (min-width: 34em) {
    .card-columns {
        -webkit-column-count: 2;
        -moz-column-count: 2;
        column-count: 2;
    }
}
@media (min-width: 48em) {
    .card-columns {
        -webkit-column-count: 3;
        -moz-column-count: 3;
        column-count: 3;
    }
}
@media (min-width: 62em) {
    .card-columns {
        -webkit-column-count: 4;
        -moz-column-count: 4;
        column-count: 4;
    }
}
@media (min-width: 75em) {
    .card-columns {
        -webkit-column-count: 5;
        -moz-column-count: 5;
        column-count: 5;
    }
}
</style>
