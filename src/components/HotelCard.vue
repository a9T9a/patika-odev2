<template>
  <b-card
    class="card"
    :img-src="require(`@/assets/${hotel.images[0]}`)"
    img-left
  >
    <b-container class="my-0 ml-1 h-100 w-100">
      <b-row class="my-0 fontcolor justify-content-start" no-gutters>
        <h3 class="name">{{ hotel.name }}</h3>
      </b-row>
      <b-row class="mt-4 fontcolor" no-gutters>
        <i class="fa fa-map-marker fa-lg mr-2" aria-hidden="true"></i>
        {{ hotel.location }}
      </b-row>
      <b-row class="mt-4 fontcolor" no-gutters>
        <span
          v-for="(s1, i) in Number(hotel.rating)"
          :key="'1' + i"
          class="fa fa-star fa-lg checked"
        ></span>
        <span
          v-for="(s2, j) in 5 - Number(hotel.rating)"
          :key="'2' + j"
          class="fa fa-star-o fa-lg"
        ></span>
      </b-row>
      <b-row class="mt-4 fontcolor" no-gutters>
        <h4 style="font-weight:bold">
          {{ hotel.price }} <small><strong>TL</strong></small>
        </h4>
      </b-row>
    </b-container>
    <div class="choose" @click="toHotel(hotel.id)">
      <p class="c-text">Seç</p>
    </div>
  </b-card>
</template>

<script>
export default {
  props: ["hotel"],
  data() {
    return {};
  },
  methods: {
    toHotel(id) {
      //redirect to hotel page
      this.$router.push({ name: "Hotel", params: { id: id } });
    },
  },
};
</script>

<style>
.card {
  position: relative;
  overflow: hidden;
  height: 235px;
  width: 100%;
  background-color: rgb(240, 240, 240);
  margin-top: 1vmax;
  padding: 0;
  display: flex;
  flex-direction: row;
  box-shadow: 0 0 20px -5px rgb(200, 200, 200);
  border: 1px solid rgb(230, 230, 230);
}
.fontcolor {
  color: rgb(15, 125, 160);
}
.brdr {
  border: 1px solid red;
}
.choose {
  position: absolute;
  bottom: -3px;
  right: -3px;
  height: 50%;
  width: 10%;
  display: flex;
  align-items: flex-end;
  border-style: solid;
  border-width: 0 0 120px 120px;
  border-color: transparent transparent rgb(15, 125, 160) transparent;
  filter: drop-shadow(-2px -2px 3px grey);
  cursor: pointer;
  transition: all 0.1s;
}
.choose:hover {
  transform: translate(-2px, -2px);
  filter: drop-shadow(-1px -1px 1.5px grey);
}
.c-text {
  position: absolute;
  bottom: -110px;
  right: 15px;
  color: whitesmoke;
  font-size: 23px;
  font-weight: 600;
  margin-right: 2%;
  margin-bottom: 2%;
  z-index: 1;
  cursor: pointer;
  user-select: none;
  text-shadow: 0px 0 3px rgb(80, 59, 59);
  background-clip: text;
}
.name {
  width: 100%;
  font-weight: 600;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  text-align: left;
}

@media screen and (max-width: 576px) {
  h3 {
    font-size: 23px;
  }
  .fa-lg {
    font-size: 1.1rem;
  }
  .card {
    max-width: 400px;
    min-width: 280px;
    height: 125vw;
    min-height: 300px;
    max-height: 500px;
    margin-bottom: 30px;
    display: block;
  }
  .card-img-left {
    width: 100%;
  }
}
</style>
