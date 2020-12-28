<template>
  <div class="grid">
    <div class='stays' v-for="stay in stays" :key="stay.index">
      <div class="stay__imgContainer">
        <img :src="stay.photo" alt="" class="stay__img">
      </div>
      <div class="stay__carac">
        <span class="stay__super" v-if="stay.superHost">SUPER HOST</span>
        <p class="stay__room">{{ stay.type }}</p>
        <div class="stay__rate">
          <span class="material-icons stay__star">
            star
          </span>
          <p class="stay__note">{{ stay.rating }}</p>
        </div>
      </div>
      <p class="stay__desc">{{ stay.title }}</p>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'Stays',
  props:["stays", "defaultStays"],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.grid{
  display: grid;
  grid-template-columns: repeat(3, 1fr);

  column-gap: 32px;
  row-gap: 49px;

  margin-bottom: 85px;
}

@media screen and (max-width: 1000px) {
  .grid{
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (max-width: 622px) {
  .grid{
    grid-template-columns: repeat(1, 1fr);
  }
}

.stays{
  width: 100%;
  height: 343px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  cursor: pointer;
}

.stays:hover  .stay__img{
  transform: scale(1.2);
}

.stay__imgContainer{
  overflow: hidden;
  border-radius: 24px;
  width: 100%;
  height: 269px;
}

.stay__img{
  width: 100%;
  height: 100%;
  object-fit: cover;
  margin-bottom: 15px;

  transition: all 0.4s ease-in-out;
}

.stay__carac{
  display: flex;
  align-items: center;


  position: relative;
}

.stay__rate{
  display: flex;
  align-items: center;

  position: absolute;
  right: 0;
}

.stay__super{
  padding: 6px 10px;
  border: 1px solid #4F4F4F;
  border-radius: 12px;

  margin-right: 11px;

  font-size: 12px;
  font-weight: 700;
}

.stay__star{
  color: #EB5757;
  margin-right: 7px;
  font-size: 19px;
}

.stay__room{
  font-size: 14px;
  font-weight: 500;
  color: #828282;
}

.stay__desc{
  font-size: 16px;
  font-weight: 600;
  color: #333;
}
  

</style>
