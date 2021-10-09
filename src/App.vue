<template>
  <div class="app">
    <div class="header">
      <h1 class="">Статистика по лидам за сегодня:</h1>
    </div>

    <div class="block__counters">
      <div class="card red">
        <div>Новых</div>
        <deal-list-new
            class="count"
        />
      </div>

      <div class="card bisque">
        <div>Заключили договор<br/>(передали <br/>в разработку)</div>
        <deal-list-new-in-dev
          class="count"
        />
      </div>

      <div class="card green">
        <div>Успешных<br/>(все документы<br/>подписаны)</div>
        <deal-list-success
            class="count"
        />
      </div>
    </div>

    <div class="block">
      <div class="header">
        <h1 class="">Общая статистика по лидам:</h1>
      </div>
      <div class="block__counters">

        <div class="card yellow">
          <div>В работе</div>
          <deal-list-in-job
              class="count"
          />
        </div>

        <div class="card dark-green">
          <div>Договор/счёт<br/> отправлен</div>
          <deal-list-bill-sent
              class="count"
          />
        </div>

        <div class="card blue">
          <div>В разработке</div>
          <deal-list-in-dev
              class="count"
          />
        </div>

        <div class="card purple">
          <div>Бухгалтерия</div>
          <deal-list-in-buh
              class="count"
          />
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import DealListInJob from "@/components/DealListInJob";
import DealListNew from "@/components/DealListNew";
import DealListBillSent from "@/components/DealListBillSent";
import DealListInDev from "@/components/DealListInDev";
import DealListInBuh from "@/components/DealListInBuh";
import DealListSuccess from "@/components/DealListSuccess";
import DealListNewInDev from "@/components/DealListNewInDev";



export default {
  name: "App",
  components: {
    DealListNewInDev,
    DealListSuccess, DealListInJob, DealListNew, DealListBillSent, DealListInDev, DealListInBuh},
}
</script>

<style>
html {
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;700&display=swap');
  text-align: center;
  display: flex;
  justify-content: center;
}
body {
  font-family: 'Source Sans Pro', sans-serif;
  background-color: #1e1e2e;
  color: #fff;
  background-image: url("../public/files/bg.jpeg");
  background-size: auto;
  background-position: top;
}
p {
  margin-block-start: 0;
  margin-block-end: 0;
  margin-inline-start: 0;
  margin-inline-end: 0;
}

h1 {
  margin-block-end: 0;
}

.header {
  padding-bottom: 15px;
  padding-top: 30px;
}

.block {
  padding: 40px;
}

.count {
  font-size: 80px;
  margin-block-start: 0;
  margin-block-end: 0;
  margin-inline-start: 0;
  margin-inline-end: 0;
}
h5 {
  font-size: 28px;
  margin-block-start: 0;
  margin-block-end: 0;
  margin-inline-start: 0;
  margin-inline-end: 0;
}

.red {
  background-color: #e5515690;
  box-shadow: 0 0 30px 0 #e5515690;
  animation: morph 5s ease-in-out infinite;
}

.yellow {
  background-color: #ecba00de;
  box-shadow: 0 0 30px 0 #ecba00de;
  animation: morph 7s ease-in-out infinite;
}

.green {
  background-color: #80ab00c9;
  box-shadow: 0 0 30px 0 #80ab00c9;
  animation: morph 12s ease-in-out infinite;
}

.blue {
  background-color: #17bcffde;
  box-shadow: 0 0 30px 0 #17bcffde;
  animation: morph 5s ease-in-out infinite;
}

.purple {
  background-color: #a517ff90;
  box-shadow: 0 0 30px 0 #a517ff90;
  animation: morph 8s ease-in-out infinite;
}

.dark-green {
  background-color: #00ab6cde;
  box-shadow: 0 0 30px 0 #00ab6cde;
  animation: morph 6s ease-in-out infinite;
}

.bisque {
  background-color: #d2691ec2;
  box-shadow: 0 0 30px 0 #d2691ec2;
  animation: morph 9s ease-in-out infinite;
}

.block__counters {
  display: flex;
  justify-content: center;
}
.card {
  display: flex;
  transition: all 1s ease-in-out;
  border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
  z-index: 5;
  padding: 40px;
  margin: 20px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

@keyframes morph {
  0% {
    border-radius:  60% 40% 30% 70% / 60% 30% 70% 40%;
  }

  50% {
    border-radius:  30% 60% 70% 40% / 50% 60% 30% 60%;
  }

  100% {
    border-radius:  60% 40% 30% 70% / 60% 30% 70% 40%;
  }
}

</style>