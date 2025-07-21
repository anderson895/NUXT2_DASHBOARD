<template>
  <v-container fluid class="py-6 px-4 bg-grey-lighten-4">
    <!-- Filter Toggle -->
    <v-row class="mb-4">
      <v-col cols="12">
        <v-btn-toggle
          v-model="selectedChart"
          dense
          class="bg-white rounded-lg"
          mandatory
        >
          <v-btn value="all">ALL</v-btn>
          <v-btn value="bar">Bar Chart</v-btn>
          <v-btn value="line">Line Chart</v-btn>
          <v-btn value="pie">Pie Chart</v-btn>
          <v-btn value="doughnut">Doughnut Chart</v-btn>
        </v-btn-toggle>
      </v-col>
    </v-row>

    <v-row dense align="stretch" class="gap-4">
      <!-- Bar Chart -->
      <v-col cols="12" md="6" v-if="selectedChart === 'bar' || selectedChart === 'all'">
        <v-card class="pa-4 rounded-xl elevation-3" color="white">
          <v-card-title class="text-h6 font-weight-bold text-primary mb-2">
            <v-icon class="mr-2" color="primary">mdi-chart-bar</v-icon> Sales Overview
          </v-card-title>
          <v-card-text class="pa-0">
            <BarChart :chart-data="barData" :chart-options="chartOptions" style="height: 300px" />
          </v-card-text>
        </v-card>
      </v-col>

      <!-- Line Chart -->
      <v-col cols="12" md="6" v-if="selectedChart === 'line' || selectedChart === 'all'">
        <v-card class="pa-4 rounded-xl elevation-3" color="white">
          <v-card-title class="text-h6 font-weight-bold text-success mb-2">
            <v-icon class="mr-2" color="success">mdi-chart-line</v-icon> Revenue Growth
          </v-card-title>
          <v-card-text class="pa-0">
            <LineChart :chart-data="lineData" :chart-options="chartOptions" style="height: 300px" />
          </v-card-text>
        </v-card>
      </v-col>

      <!-- Pie Chart -->
      <v-col cols="12" md="6" v-if="selectedChart === 'pie' || selectedChart === 'all'">
        <v-card class="pa-4 rounded-xl elevation-3" color="white">
          <v-card-title class="text-h6 font-weight-bold text-deep-purple-accent-4 mb-2">
            <v-icon class="mr-2" color="deep-purple-accent-4">mdi-chart-pie</v-icon> Sales Distribution
          </v-card-title>
          <v-card-text class="pa-0">
            <PieChart :chart-data="pieData" :chart-options="chartOptions" style="height: 300px" />
          </v-card-text>
        </v-card>
      </v-col>

      <!-- Doughnut Chart -->
      <v-col cols="12" md="6" v-if="selectedChart === 'doughnut' || selectedChart === 'all'">
        <v-card class="pa-4 rounded-xl elevation-3" color="white">
          <v-card-title class="text-h6 font-weight-bold text-orange-darken-2 mb-2">
            <v-icon class="mr-2" color="orange-darken-2">mdi-chart-donut</v-icon> Market Share
          </v-card-title>
          <v-card-text class="pa-0">
            <DoughnutChart :chart-data="doughnutData" :chart-options="chartOptions" style="height: 300px" />
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import BarChart from '~/components/BarChart.vue'
import LineChart from '~/components/LineChart.vue'
import PieChart from '~/components/PieChart.vue'
import DoughnutChart from '~/components/DoughnutChart.vue'

export default {
  components: { BarChart, LineChart, PieChart, DoughnutChart },
  data() {
    return {
      selectedChart: 'all', // default view
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false
      },
      barData: {
        labels: ['Jan', 'Feb', 'Mar'],
        datasets: [{ label: 'Sales', backgroundColor: '#42A5F5', data: [40, 20, 12] }]
      },
      lineData: {
        labels: ['Q1', 'Q2', 'Q3'],
        datasets: [{ label: 'Growth', borderColor: '#66BB6A', data: [10, 40, 30], fill: false }]
      },
      pieData: {
        labels: ['Product A', 'Product B', 'Product C'],
        datasets: [{ backgroundColor: ['#FF6384', '#36A2EB', '#FFCE56'], data: [30, 50, 20] }]
      },
      doughnutData: {
        labels: ['Asia', 'Europe', 'America'],
        datasets: [{ backgroundColor: ['#AB47BC', '#FFA726', '#26A69A'], data: [40, 30, 30] }]
      }
    }
  }
}
</script>
