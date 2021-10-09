<template>
    <div class="deals">
      <div v-for="InJob in InJobDeals">
        <p>{{ InJob.total }}</p>
      </div>
    </div>
</template>

<script>
import axios from 'axios';

const axiosInstance = axios.create({
  baseURL: process.env.VUE_APP_URL
});

export default {
  name: "DealListInDev",
  props: {
    inJobs: {
      type: Object,
    }
  },
  data () {
    return {
      InJobDeals: [],
    }
  },
  methods: {
    async getDealsInJob() {
      try {
        this.InJobDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_32473621');
        setInterval(async () => {
          this.InJobDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=getinfo.amocrm.ru_32473621');
        }, 3600000)
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.getDealsInJob();
  }
}
</script>

<style scoped>

</style>