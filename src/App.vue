<template>
  <div id="app">
    <ModaleHeader v-bind:openCloseModale="openCloseModale" v-bind:modaleState="modaleState" v-bind:selected="selected" v-bind:submit="submit" />
    <Header v-bind:city="city" v-bind:guests="guests" v-bind:stays="stays" v-bind:defaultStays="defaultStays" v-bind:submit="submit" v-bind:openCloseModale="openCloseModale" v-bind:modaleState="modaleState"/>
    <div class="appTitle">
      <h1 v-if="city != undefined" class="title">Stays in {{ city }} </h1>
      <h1 v-else class="title">Stays in Finland </h1>
      <p class="number">{{ stays.length }} stays</p>
    </div>
    <Stays v-bind:stays="stays" v-bind:defaultStays="defaultStays"/>
    <div class="separation-line"></div>
    <p class="my-name">Thomas Arbeit @ DevChallenges.io</p>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import ModaleHeader from './components/ModaleHeader.vue'
import Stays from './components/Stays.vue'

export default {
  name: 'App',
  components: {
    Header,
    Stays,
    ModaleHeader
  },
  data(){
    return{
      cities: "",
      city: "",
      guests: "",
      stays: "",
      defaultStays: [
              {
                "city": "Helsinki",
                "country": "Finland",
                "superHost": false,
                "title": "Stylist apartment in center of the city",
                "rating": 4.4,
                "maxGuests": 3,
                "type": "Entire apartment",
                "beds": 2,
                "photo": "https://images.unsplash.com/photo-1505873242700-f289a29e1e0f?ixlib=rb-1.2.1&auto=format&fit=crop&w=2255&q=80"
              },
              {
                "city": "Turku",
                "country": "Finland",
                "superHost": false,
                "title": "Nice apartment in center of Helsinki",
                "rating": 4.2,
                "maxGuests": 5,
                "type": "Entire apartment",
                "beds": 3,
                "photo": "https://images.unsplash.com/photo-1554995207-c18c203602cb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80"
              },
              {
                "city": "Helsinki",
                "country": "Finland",
                "superHost": true,
                "title": "Arty interior in 1900 wooden house",
                "rating": 4.5,
                "maxGuests": 10,
                "type": "Entire house",
                "beds": 6,
                "photo": "https://images.unsplash.com/photo-1505691938895-1758d7feb511?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80"
              },
              {
                "city": "Helsinki",
                "country": "Finland",
                "superHost": false,
                "title": "Apartment next to market spuare",
                "rating": 4.48,
                "maxGuests": 3,
                "type": "Entire apartment",
                "beds": null,
                "photo": "https://images.unsplash.com/photo-1556020685-ae41abfc9365?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=934&q=80"
              },
              {
                "city": "Turku",
                "country": "Finland",
                "superHost": true,
                "title": "Villa Aurora guest-house",
                "rating": 4.75,
                "maxGuests": 9,
                "type": "Entire house",
                "beds": null,
                "photo": "https://images.unsplash.com/photo-1513694203232-719a280e022f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2249&q=80"
              },
              {
                "city": "Vaasa",
                "country": "Finland",
                "superHost": true,
                "title": "A cosy family house",
                "rating": 4.95,
                "maxGuests": 6,
                "type": "Entire house",
                "beds": null,
                "photo": "https://images.unsplash.com/photo-1524758631624-e2822e304c36?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80"
              },
              {
                "city": "Vaasa",
                "country": "Finland",
                "superHost": false,
                "title": "Lovely Studio near Railway Station",
                "rating": 4.68,
                "maxGuests": 2,
                "type": "Private room",
                "beds": null,
                "photo": "https://images.unsplash.com/photo-1505693314120-0d443867891c?ixlib=rb-1.2.1&auto=format&fit=crop&w=2591&q=80"
              },
              {
                "city": "Oulu",
                "country": "Finland",
                "superHost": false,
                "title": "Peaceful little home in city center",
                "rating": 4.12,
                "maxGuests": 6,
                "type": "Entire house",
                "beds": 3,
                "photo": "https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80"
              },
              {
                "city": "Oulu",
                "country": "Finland",
                "superHost": false,
                "title": "Beautiful new studio apartment nearby the center",
                "rating": 4.49,
                "maxGuests": 2,
                "type": "Entire apartment",
                "beds": 1,
                "photo": "https://images.unsplash.com/photo-1507089947368-19c1da9775ae?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2255&q=80"
              },
              {
                "city": "Oulu",
                "country": "Finland",
                "superHost": true,
                "title": "Cozy woodhouse flat with wooden sauna",
                "rating": 4.38,
                "maxGuests": 4,
                "type": "Entire house",
                "beds": null,
                "photo": "https://images.unsplash.com/photo-1522156373667-4c7234bbd804?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjF9&auto=format&fit=crop&w=930&q=80"
              },
              {
                "city": "Vaasa",
                "country": "Finland",
                "superHost": false,
                "title": "Brand new studio apartment near the harbour",
                "rating": 4.89,
                "maxGuests": 6,
                "type": "Entire apartment",
                "beds": 3,
                "photo": "https://images.unsplash.com/photo-1494203484021-3c454daf695d?ixlib=rb-1.2.1&auto=format&fit=crop&w=2250&q=80"
              },
              {
                "city": "Helsinki",
                "country": "Finland",
                "superHost": false,
                "title": "Beautiful and comfortable old wooden house",
                "rating": 4.63,
                "maxGuests": 10,
                "type": "Entire house",
                "beds": null,
                "photo": "https://images.unsplash.com/photo-1516455590571-18256e5bb9ff?ixlib=rb-1.2.1&auto=format&fit=crop&w=2250&q=80"
              },
              {
                "city": "Turku",
                "country": "Finland",
                "superHost": false,
                "title": "Turku Nordic Home near city center",
                "rating": 4.24,
                "maxGuests": 5,
                "type": "Entire apartment",
                "beds": 3,
                "photo": "https://images.unsplash.com/photo-1519643381401-22c77e60520e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjE3MzYxfQ&auto=format&fit=crop&w=2253&q=80"
              },
              {
                "city": "Turku",
                "country": "Finland",
                "superHost": true,
                "title": "Nice 2 room apartment close to everything",
                "rating": 4.34,
                "maxGuests": 6,
                "type": "Entire apartment",
                "beds": 3,
                "photo": "https://images.unsplash.com/photo-1523755231516-e43fd2e8dca5?ixlib=rb-1.2.1&auto=format&fit=crop&w=1275&q=80"
              }
    ],
      modaleState : false,
      selected: ""
    }
  },
  mounted(){
    this.stays = this.defaultStays
  },
  methods:{
    submit(city, guest){
      console.log(guest)
      this.stays = []
      if (city == "" && guest == ""){
        console.log("Vous n'avez pas saisis d'information")
        this.stays = this.defaultStays
      } else if (city != "" && guest == ""){
        console.log("Vous n'avez saisis que la ville")
        for (let i = 0; i < this.defaultStays.length; i++){
          if (this.defaultStays[i].city == city){
            this.stays.push(this.defaultStays[i]);
          }
        }
      } else if (city == "" && guest != ""){
        console.log("Vous n'avez saisis que les invités")
        for (let i = 0; i < this.defaultStays.length; i++){
          if (this.defaultStays[i].maxGuests >= guest){
            this.stays.push(this.defaultStays[i]);
          }
        }
      } else {
        console.log("Vous avez saisis la ville et les invités")
        for (let i = 0; i < this.defaultStays.length; i++){
          if ((this.defaultStays[i].city == city) && (this.defaultStays[i].maxGuests >= guest)){
            this.stays.push(this.defaultStays[i])
          }
        }
      }

      this.city = city;
      this.guests = guest;
    },
    openCloseModale(){
      this.modaleState = !this.modaleState
    },
    changeCity(){
      this.selected = document.getElementById('city');
    }
  }
}

</script>

<style >
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
  
  html{
    font-family: "Montserrat";
  }

  #app{
    max-width: 1300px;
    padding: 0 25px;

    margin: 0 auto;
  }

  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .title{
    font-size: 24px;
    font-weight: 700;
  }

  .appTitle{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 32px;
  }

  .number{
    font-size: 14px;
    font-weight: 500;
  }

  .separation-line{
    margin: 0 auto 23px;
    max-width: 402px;
    height: 1px;
    background-color: #BDBDBD;
  }

  .my-name{
    font-size: 14px;
    font-weight: 600;
    color: #A9A9A9;

    text-align: center;

    margin-bottom: 19px;
  }
</style>
