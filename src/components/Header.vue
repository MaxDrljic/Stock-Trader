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
      <strong class="navbar-text navbar-right">Funds: {{ funds }}</strong>
      <ul class="nav navbar-nav navbar-right">
        <li>
          <a href="#" class="nav-link">End Day</a>
        </li>
        <li class="dropdown">
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
              <a href="#" class="nav-link">Save Data</a>
            </li>
            <li>
              <a href="#" class="nav-link">Load Data</a>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  }
};
</script>

<style>
</style>
