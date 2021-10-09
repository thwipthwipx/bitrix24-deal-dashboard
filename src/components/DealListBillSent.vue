<template>
    <div class="deals">
      <div v-for="BillDeal in BillDeals">
        <p>{{ BillDeal.total }}</p>
      </div>
    </div>

</template>

<script>
import axios from 'axios';

const axiosInstance = axios.create({
  baseURL: process.env.VUE_APP_URL
});

export default {
  name: "DealListBillSent",
  props: {
    BillDeals: {
      type: Object,
    }
  },
  data () {
    return {
      BillDeals: [],
    }
  },
  methods: {
    async getDealsInBillSent() {
      try {
        this.BillDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_30385663');
        setInterval(async () => {
          this.BillDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_30385663');
        }, 3600000)
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.getDealsInBillSent();
  }
}
</script>

<style scoped>

</style>