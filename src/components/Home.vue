<template>
 <div>
    <h1>Trade or view your portfolio</h1>
    <h6>You may Save & Load your Data</h6>
    <h6> Click on 'END DAY' to begin a  new Day</h6>
    <hr>
    <p>Your Funds: {{funds}}</p>
 </div>
</template>

<script>
export default {
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  }
}
</script>