<template>
  <div v-if="modaleState == true" class="modale">
    <div class="modale__header">
      <div class="modale__center">
        <form action="" class="modale__form">
          <div class="modale__section">
            <label  for="city" class="modale__label">CITY: {{ city }}</label>
              <select v-model="city"  id="city" name="city" class="modale__select">
                <option disabled value="">Chose Your City</option>
                <option value="">Anywhere</option>
                <option value="Helsinki">Helsinki</option>
                <option value="Oulu">Oulu</option>
                <option value="Vaasa">Vaasa</option>
                <option value="Turku">Turku</option>
              </select>
          </div>
          
          <div class="modale__section">
            <label  for="guest" class="modale__label">GUESTS: {{ guest }}</label>
              <select v-model="guest"  id="guest" name="guest" class="modale__select">
                <option disabled value="">Add guests</option>
                <option value="">Peu importe</option>
                <option value="1">1</option>
                <option value="2">2</option>
                <option value="3">3</option>
                <option value="4">4</option>
                <option value="5">5</option>
              </select>
          </div>

          <div class="modale__section modale__section--last">
            <button class="modale__button" type="submit" v-on:click.prevent="submit(city, guest), openCloseModale() ">
              <span class="material-icons">
                search
              </span>
              Search
              </button>
          </div>
          

          
        </form>
      </div>
    </div>
    <div class="modale__transparent" v-on:click="openCloseModale()"></div>
  </div>
</template>





<script>
export default {
  name: 'Header',
  props:["openCloseModale","modaleState", "selected", "changeCity", "submit"],
  data(){
    return{
      city:"",
      guest:""
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

  @import url('https://fonts.googleapis.com/css2?family=Mulish:ital,wght@0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

  .modale{
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;

    z-index: 3;
  }

  .modale__header{
    width: 100%;
    min-height: 460px;
    background-color: white;
    animation: animate 0.3s ease-in-out;
  }

  .modale__transparent{
    position: absolute;
    top:0;
    right:0;
    bottom: 0;
    left:0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.438);

    z-index: -1;
  }

  .modale__center{
    max-width: 1300px;
    width: 100%;
    padding: 93px 25px 0px;
    margin: 0 auto;
  }

  .modale__form{
    display: flex;
    box-shadow: 0px 1px 6px rgba(0,0,0,0.1);
    border-radius: 16px;

    overflow: hidden;
  }

  @media screen and (max-width: 465px){
    .modale__form{
      flex-direction: column;
    }

    .modale__section{
      border-bottom: 1px solid  #F2F2F2;
      border-right: none;
    }
  }

  .modale__select{
    display: block;
  }

  .modale__section{
    flex: 1;
    border-right: 1px solid #F2F2F2;
    position: relative;
  }

  .modale__section--last{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modale__button{
    display: flex;
    height: 87%;
    background-color: rgba(235, 87, 87, 0.9);
    border: none;
    color: white;
    font-size: 14px;
    font-weight: 500;
    font-family: 'Mulish';
    line-height: 17px;

    border-radius: 16px;

    padding: 16px 24px 14px 27px;

    align-items: center;

    cursor: pointer;
  }

  .modale__button span{
    margin-right: 11px;
  }

  .modale__label{
    color: #333333;
    font-weight: 800;
    font-size: 9px;
    line-height: 11.3px;

    position: absolute;
    top: 12px;
    left: 26px;
  }

  .modale__select{
    border: none;
    width: 100%;

    padding-top: 27px;
    padding-bottom: 10px;
    padding-left: 25px;

    border-radius: 16px;

    -webkit-appearance: none; 

    cursor: pointer;
  }

  .modale__select > option{
    box-shadow: none;
  }

  @keyframes animate {
    from{
      transform: translateY(-100%);
    }
    to{
      transform: translate(0);
    }
  }



</style>
