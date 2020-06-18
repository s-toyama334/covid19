<template>
  <v-col cols="12" md="6" class="DataCard">
    <confirmed-cases-card
      :title="$t('青森県内の検査陽性者の状況')"
      :title-id="'details-of-confirmed-cases'"
      :date="Data.patients.date"
    >
      <confirmed-cases-table
        :aria-label="$t('青森県内の検査陽性者の状況')"
        v-bind="confirmedCases"
      />
    </confirmed-cases-card>
    <template v-slot:description>
      {{ $t('※土・日・祝日を除く庁舎開庁日の1週間累計数') }}
    </template>
  </v-col>
</template>

<script>
import Data from '@/data/data.json'
import formatConfirmedCases from '@/utils/formatConfirmedCases'
import ConfirmedCasesCard from '@/components/ConfirmedCasesCard.vue'
import ConfirmedCasesTable from '@/components/ConfirmedCasesTable.vue'

export default {
  components: {
    ConfirmedCasesCard,
    ConfirmedCasesTable
  },
  data() {
    // 検査陽性者の状況
    const confirmedCases = formatConfirmedCases(Data.main_summary)

    const data = {
      Data,
      confirmedCases
    }
    return data
  }
}
</script>
