<template>
  <nav class="navbar navbar-default">
    <!-- <a class="navbar-brand" href="#">Stock</a> -->
    <router-link to="/" class="navbar-brand">Stock</router-link>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="nav navbar-nav">
        <router-link to="/portfolio" class="nav-item" activeClass="active" tag="li">
          <a class="nav-link">Portfolio</a>
        </router-link>
        <router-link to="/stocks" class="nav-item" activeClass="active" tag="li">
          <a class="nav-link">Stocks</a>
        </router-link>
      </ul>
      <strong class="nav-bar-text nav-bar-right">Funds: {{ funds }}</strong>
      <ul class="nav navbar-nav navbar-right">
        <li>
          <a href="#">End Day</a>
        </li>
        <li
          class="dropdown"
          :class="{open:isDropDownOpen}"
          @click="isDropDownOpen =!isDropDownOpen"
        >
          <a
            href="#"
            class="dropdown-toggle"
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
              <a href="#" @click="saveData">Save Data</a>
            </li>
            <li>
              <a href="#" @click="loadData1">Load Data</a>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </nav>
</template>
<script>
import {mapActions} from 'vuex';
export default {
  data() {
    return {
      isDropDownOpen: false
    };
  },
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  },
  methods: {
    ...mapActions([
      'loadData'
    ]),
    saveData() {
      const data = {
        funds:this.$store.getters.funds,
        stockPortfolio: this.$store.getters.stockPortfolio,
        stocks: this.$store.getters.stocks
      }
      this.$http.put('data.json',data);
    }, 
    loadData1() {
      this.loadData();
    }
  }
};
</script>