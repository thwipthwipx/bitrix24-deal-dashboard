<template>
    <div class="deals">
      <div v-for="NewDeal in NewDeals">
        <p>{{ NewDeal.total }}</p>
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
  name: "DealListNew",
  props: {
    NewDeals: {
      type: Object,
    }
  },
  data () {
    return {
      NewDeals: [],
    }
  },
  methods: {
    getDealsNewDeals: async function () {
      try {
        this.NewDeals = await axiosInstance.get('crm.deal.list.json?filter[>DATE_CREATE]='+moment().format('DD-MM-YYYY'));
        setInterval(async () => {
          this.NewDeals = await axiosInstance.get('crm.deal.list.json?filter[>DATE_CREATE]='+moment().format('DD-MM-YYYY'));
        }, 300000)
      } catch (e) {
        alert('Ошибка')
      }
    }
  },
  mounted() {
    this.getDealsNewDeals();
  }
}
</script>

<style scoped>

</style>