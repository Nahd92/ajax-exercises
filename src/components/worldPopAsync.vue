<template>
  <div class="worldPop">
    <h1>HELLO</h1>
    <div v-for="pop in worldPops" v-bind:key="pop.id">
      <div class="country"><strong>Country</strong>: {{ pop.countryName }}</div>
      <div class="country"><strong>Population</strong>: {{ pop.value }}</div>
      <br />
    </div>
  </div>
</template>

<script>
export default {
  name: "worldPop-async",
  data: () => ({
    message: "",
    worldPops: [],
  }),
  async mounted() {
    const url = "https://countriesnow.space/api/v0.1/countries/population";
    try {
      const response = await fetch(url);
      const data = await response.json();

      for (let i = 1; i < data.data.length; i++) {
        const countryName = data.data[i].country;
        const countriespopulationCounts = data.data[i].populationCounts;
        countriespopulationCounts.forEach((population) => {
          if (population.year == "2018") {
            const value = new Intl.NumberFormat().format(population.value);
            this.worldPops.push({ countryName, value });
          }
        });
      }
    } catch (error) {
      console.log("fetching didnt work");
      this.message = "Api call didnt work";
    }
  },
};
</script>

<style lang="scss" scoped>
</style>