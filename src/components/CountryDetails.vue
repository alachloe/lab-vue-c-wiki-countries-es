<template>
  <div>
    <div class="col-7">
      <img src="https://restcountries.eu/data/fra.svg" alt="country flag" style="width: 300px" />
      <h1>France</h1>
      <table class="table">
        <thead></thead>
        <tbody>
          <tr>
            <td style="width: 30%">Capital</td>
            <td>{{ country.name }}</td>
          </tr>
          <tr>
            <td>Area</td>
            <td>
              {{ country.area }}<sup>2</sup>
            </td>
          </tr>
          <tr>
            <td>Borders</td>
            <td>
              <ul>
                <li><a href="/AND">Andorra</a></li>
                <li><a href="/BEL">Belgium</a></li>
                <li><a href="/DEU">Germany</a></li>
                <li><a href="/ITA">Italy</a></li>
                <li><a href="/MCO">Monaco</a></li>
                <li><a href="/ESP">Spain</a></li>
                <li><a href="/CHE">Switzerland</a></li>
              </ul>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      country: null,
    };
  },
  mounted() {
    const alpha3Code = this.$route.params.alpha3Code;
    this.getCountryDetails(alpha3Code);
  },
  methods: {
    getCountryDetails(alpha3Code) {
      axios
        .get(`https://ih-countries-api.herokuapp.com/countries/${alpha3Code}`)
        .then((response) => {
          this.country = response.data;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
