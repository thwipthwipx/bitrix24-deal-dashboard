<template>
    <div class="deals">
      <div v-for="NewInDevDeal in NewInDevDeals">
        <p>{{ NewInDevDeal.total }}</p>
      </div>
    </div>

</template>

<script>
import axios from 'axios';
import moment from "moment";

const axiosInstance = axios.create({
  baseURL: process.env.VUE_APP_URL
});

export default {
  name: "DealListNewInDev",
  props: {
    NewInDevDeals: {
      type: Object,
    }
  },
  data () {
    return {
      NewInDevDeals: [],
    }
  },
  methods: {
    getDealsNewInDev: async function () {
      try {
        this.NewInDevDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_30471334&filter[UF_CRM_1612265405255]='+moment().format('DD-MM-YYYY'));
        setInterval(async () => {
          this.NewInDevDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_30471334&filter[UF_CRM_1612265405255]='+moment().format('DD-MM-YYYY'));
        }, 300000)
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.getDealsNewInDev();
  }
}
</script>

<style scoped>

</style>