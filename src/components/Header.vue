<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link to="/" class="navbar-brand">Stock Trader</router-link>

    <div class="collapse navbar-collapse">
      <ul class="navbar-nav mr-auto">
        <router-link to="/portfolio" activeClass="active" tag="li">
          <a class="nav-link">Portfolio</a>
        </router-link>
        <router-link to="/stocks" activeClass="active" tag="li">
          <a class="nav-link">Stocks</a>
        </router-link>
      </ul>
      <strong class="navbar-text navbar-right">Funds: {{ funds | currency }}</strong>
      <ul class="nav navbar-nav navbar-right">
        <li
          class="dropdown"
          :class="{open: isDropdownOpen}"
          @click="isDropdownOpen != isDropdownOpen"
        >
          <a
            href="#"
            class="dropdown-toggle nav-link"
            data-toggle="dropdown"
            role="button"
            aria-haspopup="true"
            aria-expanded="false"
          >
            Save & Load
            <span class="caret"></span>
          </a>
          <ul class="dropdown-menu">
            <li>
              <a href="#" class="nav-link" @click="saveData">Save Data</a>
            </li>
            <li>
              <a href="#" class="nav-link" @click="loadData">Load Data</a>
            </li>
          </ul>
        </li>
        <li>
          <a href="#" @click="endDay" class="nav-link">End Day</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
import { mapActions } from "vuex";

export default {
  data() {
    return {
      isDropdownOpen: false
    };
  },
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  },
  methods: {
    ...mapActions(["randomizeStocks"]),
    endDay() {
      this.randomizeStocks();
    },
    saveData() {
      const data = {
        funds: this.$store.getters.funds,
        stockPortfolio: this.$store.getters.stockPortfolio,
        stocks: this.$store.getters.stocks
      };
      this.$http.put("data.json", data);
    },
    loadData() {}
  }
};
</script>

<style>
</style>
