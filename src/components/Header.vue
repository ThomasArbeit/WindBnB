<template>
  <div class='header'>
    <div class="header__logo">
      <img src="../assets/logo.png" alt="">
    </div>

    <div class="header__nav" id="header__nav" v-on:click="openCloseModale">
      <p v-if="city != '' " class="header__link header__link--active">{{ city }}, Finland</p>
      <p v-else class="header__link " >Chose your city</p>

      <p v-if="guests != '' " class="header__link header__link--active ">{{ guests }} guests</p>
      <p v-else class="header__link">Add guests</p>
      <div class="header__button">
        <span class="material-icons">
          search
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props:["city", "guests", "defaultStays", "stays", "submit", "modaleState", "openCloseModale"],
  methods:{
    big(){
      let headerNav = document.getElementById('header__nav');
      if (headerNav.style.width == "100%"){
        headerNav.style.width = "";
      } else {
        document.getElementById('header__nav').style.width = "100%";
      }
      document.getElementById('header__nav').style.transition = "all 2s ease-in-out";
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

  @import url('https://fonts.googleapis.com/css2?family=Mulish:ital,wght@0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

  .header{
    width: 100%;

    display: flex;
    justify-content: space-between;
    align-items: center;

    margin-top: 32px;
    margin-bottom: 61px;

    font-family: 'Mulish';
  }

  .header__nav{
    display: flex;
    align-items: center;
    border-radius: 16px;
    box-shadow: 0px 1px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;

    cursor: pointer;
  }

  .header__link{
    padding: 18px 16px;
    border-right: 1px solid #F2F2F2;
    font-size: 14px;
    color: #BDBDBD;
    font-weight: 400;
  }

  .header__link:hover{
    background-color: #f1f1f1;
    color: #EB5757;
  }

  .header__link--active{
    color: #333;
  }

  .header__button{
    border: none;
    background-color: transparent;
    color: #EB5757;
    height: 100%;
    padding: 0 16px;
  }

</style>
