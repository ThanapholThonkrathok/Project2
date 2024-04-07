<script setup>
import AnalyticsFinanceTabs from '@/views/dashboard/AnalyticsFinanceTab.vue'
import AnalyticsOrderStatistics from '@/views/dashboard/AnalyticsOrderStatistics.vue'
import AnalyticsTotalRevenue from '@/views/dashboard/AnalyticsTotalRevenue.vue'
import AnalyticsTransactions from '@/views/dashboard/AnalyticsTransactions.vue'

// 👉 Images //
import chart from '@images/cards/chart-success.png'
import card from '@images/cards/credit-card-primary.png'
import paypal from '@images/cards/paypal-error.png'
import wallet from '@images/cards/wallet-info.png'

import { onMounted, ref } from 'vue'

const fetchData = () => {
  fetch('http://202.29.238.30:1880/getdata')
    .then(response => {
      if (response.status === 200) {
        response.json().then(json => {
          temperature.value = parseFloat(json["Temp="]).toFixed(2)
          doValue.value = parseFloat(json["DO="]).toFixed(2)
          phValue.value = parseFloat(json["pH="]).toFixed(2)
          tdsValue.value = parseFloat(json["TDS="]).toFixed(2)
        })
      } else {
        throw new Error('Request failed.')
      }
    })
    .catch(error => {
      console.log(error)
    })
}

const temperature = ref(0)
const doValue = ref(0)
const phValue = ref(0)
const tdsValue = ref(0)

onMounted(() => {
  setInterval(fetchData, 3000)
})
</script>

<template>
  <VRow>
    <!-- 👉 main -->
    <VCol
      cols="12"
      md="8"
    >
      <AnalyticsTotalRevenue />
    </VCol>

    <VCol
      cols="12"
      sm="4"
    >
      <VRow>
        <!-- 👉 Profit -->
        <VCol
          cols="12"
          md="6"
        >
          <CardStatisticsVertical
            title="pH"
            :image="chart"
            :stats="`${temperature}`"
            :change="doValue"
          />
        </VCol>

        <!-- 👉 Sales -->
        <VCol
          cols="12"
          md="6"
        >
          <CardStatisticsVertical
            title="DO"
            :image="wallet"
            :stats="`${doValue}`"
            :change="doValue"
          />
        </VCol>
        <!-- 👉 Sales -->
        <VCol
          cols="12"
          md="6"
        >
          <CardStatisticsVertical
            title="TDS"
            :image="paypal"
            :stats="`${tdsValue}`"
            :change="tdsValue"
          />
        </VCol>
        <!-- 👉 Sales -->
        <VCol
          cols="12"
          md="6"
        >
          <CardStatisticsVertical
            title="Temp"
            :image="card"
            :stats="`${phValue}`"
            :change="phValue"
          />
        </VCol>
      </VRow>
    </VCol>

    <!-- 👉 Total Revenue -->


    <VCol
      cols="12"
      sm="8"
      md="4"
      order="1"
      order-md="2"
    >
      <VRow>
        <!-- 👉 Profit Report -->
        <VCol
          cols="12"
          sm="12"
        />
      </VRow>
    </VCol>

    <!-- 👉 Order Statistics -->
    <VCol
      cols="12"
      md="4"
      sm="6"
      order="3"
    >
      <AnalyticsOrderStatistics />
    </VCol>

    <!-- 👉 Tabs chart -->
    <VCol
      cols="12"
      md="4"
      sm="6"
      order="3"
    >
      <AnalyticsFinanceTabs />
    </VCol>

    <!-- 👉 Transactions -->
    <VCol
      cols="12"
      md="4"
      sm="6"
      order="3"
    >
      <AnalyticsTransactions />
    </VCol>
  </VRow>
</template>
