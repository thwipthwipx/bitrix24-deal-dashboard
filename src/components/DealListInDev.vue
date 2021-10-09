<template>
    <div class="deals">
      <div v-for="InDev in InDevDeals">
        <p>{{ InDev.total }}</p>
      </div>
    </div>

</template>

<script>
import axios from 'axios';

const axiosInstance = axios.create({
  baseURL: process.env.VUE_APP_URL
});

export default {
  name: "DealListNew",
  props: {
    InDevDeals: {
      type: Object,
    }
  },
  data () {
    return {
      InDevDeals: [],
    }
  },
  methods: {
    getDealsInDev: async function () {
      try {
        this.InDevDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_30471334');
        setInterval(async () => {
          this.InDevDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_30471334');
        }, 3600000)
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.getDealsInDev();
  }
}
</script>

<style scoped>

</style>