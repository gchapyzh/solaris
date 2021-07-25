<template>
<div>
  <p v-if="event.data.credits">
    A galactic cycle is complete. You have received <span class="text-success">${{Math.floor(event.data.credits.creditsEconomy)}}</span> from your
    economic infrastructure and <span class="text-success">${{Math.floor(event.data.credits.creditsBanking)}}</span> from your banking technology.
  </p>
  
  <p v-if="event.data.credits && Math.floor(event.data.credits.creditsSpecialists)">
    You have received <strong><span class="text-success">{{Math.floor(event.data.credits.creditsSpecialists)}}</span> specialist token(s)</strong> from your
    specialists technology.
  </p>

  <p v-if="event.data.experimentTechnology">
    Your experimental scientists have stumbled across a new discovery which has unlocked
    <span class="text-warning">{{event.data.experimentAmount}} points</span> of research in the field of <span class="text-info">{{getTechnologyFriendlyName(event.data.experimentTechnology)}}</span>.
  </p>
  
  <p v-if="event.data.carrierUpkeep && Math.floor(event.data.carrierUpkeep.totalCost)">
    The upkeep of <span class="text-warning">{{event.data.carrierUpkeep.carrierCount}} carrier(s)</span> incurred a cost of 
    <span class="text-danger">${{Math.floor(event.data.carrierUpkeep.totalCost)}}</span>.
  </p>
</div>
</template>

<script>
import TechnologyHelper from '../../../../services/technologyHelper'

export default {
  components: {

  },
  props: {
    event: Object
  },
  methods: {
    getTechnologyFriendlyName (key) {
      return TechnologyHelper.getFriendlyName(key)
    }
  }
}
</script>

<style scoped>
</style>
