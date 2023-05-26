<template lang="pug">
.weather
  .weather__heading Weather Demo
  ul.weather__cities
    li.city
      .city__name Mountain View
      .city__info
        #location.city__name
        #description.desc
        #temp.temp 27 C
        .date Monday, 25 May
        .time 15:30
</template>

<script lang="ts">
  export default {
    data() {
      return {
        weather: {},
      };
    },

    methods: {
      fetchWeather(cityID: number) {
        let key = '{30069339f349b7c63a9fa259b56a603f}';
        fetch('https://api.openweathermap.org/data/2.5/weather?id=' + cityID + '&appid=' + key)
          .then((res) => res.json())
          .then((data) => {
            console.log(data);
            // this.weather = data;
          });
      },
      // onWindowLoad() {
      //   fetchWeather(6167865);
      // },

      // showWeather(d: any) {
      //   const celcius = Math.round(parseFloat(d.main.temp) - 273.15);
      //   const fahrenheit = Math.round((parseFloat(d.main.temp) - 273.15) * 1.8 + 32);

      //   document.getElementById('description').innerHTML = d.weather[0].description;
      //   document.getElementById('temp').innerHTML = celcius + '&deg;';
      //   document.getElementById('location').innerHTML = d.name;
      // },
    },
  };
</script>

<style style scoped lang="scss">
  .weather {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 40px;
    flex-direction: column;

    &__heading {
      color: #5c5c5c;
      align-self: center;
      font-size: 40px;
    }

    &__cities {
      width: 600px;
      height: auto;
      height: min-content;

      & .city {
        width: 100%;
        border-radius: 16px;
        border: 1px solid #5c5c5c;
        padding: 20px;
        display: flex;
        flex-direction: column;
        gap: 16px;

        &__info {
          display: grid;
          grid-template-columns: 0.5fr 1fr;
          grid-template-rows: 0.5fr 1fr;
          gap: 10px 10px;
          grid-template-areas:
            'temp date'
            'temp time';

          & .temp {
            grid-area: temp;
            font-size: 45px;
          }

          & .date {
            grid-area: date;
          }

          & .time {
            grid-area: time;
          }
        }
      }
    }
  }
</style>
