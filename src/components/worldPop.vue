<template>
  <div class="worldPop">
    <div v-for="pop in populations" v-bind:key="pop.id">
      <div class="country"><strong>Country</strong>: {{ pop.countryName }}</div>
      <div class="country"><strong>Population</strong>: {{ pop.value }}</div>
      <br />
    </div>
  </div>
</template>

<script>
export default {
  name: "worldPop",
  data: () => ({
    populations: [],
  }),
  mounted() {
    fetch("https://countriesnow.space/api/v0.1/countries/population")
      .then((response) => response.json())
      .then((data) => {
        for (let i = 1; i < data.data.length; i++) {
          const countryName = data.data[i].country;
          const countriespopulationCounts = data.data[i].populationCounts;
          countriespopulationCounts.forEach((population) => {
            if (population.year == "2018") {
              const value = new Intl.NumberFormat().format(population.value);
              this.populations.push({ countryName, value });
            }
          });
        }
      });
  },
};
</script>

<style lang="scss" scoped>
</style>