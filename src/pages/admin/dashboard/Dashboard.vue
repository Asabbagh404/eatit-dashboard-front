<template>
  <div class="dashboard">
    <div class="row row-equal">
      <div class="flex xs12 lg6">
        <dashboard-charts />
      </div>
      <div class="flex xs12 lg6">
        <dashboard-info-block />
      </div>
    </div>
    <div class="row row-equal">
      <div class="flex xs12 lg6">
        <dashboard-tabs @submit="addAddressToMap"/>
      </div>
    </div>
  </div>
</template>

<script>
import DashboardCharts from './DashboardCharts'
import DashboardInfoBlock from './DashboardInfoBlock'
import DashboardTabs from './DashboardTabs'

export default {
  name: 'dashboard',
  components: {
    DashboardCharts,
    DashboardInfoBlock,
    DashboardTabs,
  },
  methods: {
    addAddressToMap ({ city, country }) {
      this.$refs.dashboardMap.addAddress({ city: city.text, country })
    },
  },
}
</script>

<style lang="scss">
  .row-equal .flex {
    .va-card {
      height: 100%;
    }
  }

  .dashboard {
    .va-card {
      margin-bottom: 0 !important;
      &__title {
        display: flex;
        justify-content: space-between;
      }
    }
  }
</style>
