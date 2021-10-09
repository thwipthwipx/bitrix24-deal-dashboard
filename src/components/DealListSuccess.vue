<template>
    <div class="deals">
      <div v-for="SuccessDeal in SuccessDeals">
        <p>{{ SuccessDeal.total }}</p>
      </div>
    </div>

</template>

<script>
import axios from 'axios';
import moment from 'moment';

const axiosInstance = axios.create({
  baseURL: process.env.VUE_APP_URL
});
export default {
  name: "DealListSuccess",
  props: {
    SuccessDeals: {
      type: Object,
    }
  },
  data () {
    return {
      SuccessDeals: [],
    }
  },
  methods: {
    getDealsSuccess: async function () {
      try {
        this.SuccessDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=WON&filter[>DATE_MODIFY]='+moment().format('DD-MM-YYYY'));
        setInterval(async () => {
          this.SuccessDeals = await axiosInstance.get('crm.deal.list.json?filter[STAGE_ID]=WON&filter[>DATE_MODIFY]='+moment().format('DD-MM-YYYY'));
        }, 300000)
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.getDealsSuccess();
  }
}
</script>

<style scoped>

</style>