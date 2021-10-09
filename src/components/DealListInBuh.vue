<template>
    <div class="deals">
      <div v-for="InBuh in InBuhDeals">
        <p>{{ InBuh.total }}</p>
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
    InBuhDeals: {
      type: Object,
    }
  },
  data () {
    return {
      InBuhDeals: [],
    }
  },
  methods: {
    async getDealsInBuh() {
      try {
        this.InBuhDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_31457866');
        setInterval(async () => {
          this.InBuhDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_31457866');
        }, 3600000)
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.getDealsInBuh();
  }
}
</script>

<style scoped>

</style>