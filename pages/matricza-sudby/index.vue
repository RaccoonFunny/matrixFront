<script setup lang="ts">
import {ref, onBeforeMount} from 'vue'
import MatrixSelect from "~/component/matrixSelect.vue";
import MatrixSelectSmall from "~/component/matrixSelectSmall.vue";
import MatrixDiagram from "~/component/matrix-diagram.vue";
import MatrixTable from "~/component/matrix-table.vue";
import MatrixTexts from "~/component/matrix-texts.vue";

const days = ref({
  // Объект для дней в каждом месяце
  daysOfMonth: {
    "1": true, "2": false, "3": false, "4": false, "5": false, "6": false,
    "7": false, "8": false, "9": false, "10": false, "11": false, "12": false,
    "13": false, "14": false, "15": false, "16": false, "17": false, "18": false,
    "19": false, "20": false, "21": false, "22": false, "23": false, "24": false,
    "25": false, "26": false, "27": false, "28": false, "29": false, "30": false,
    "31": false
  },

  months: {
    "Январь": true, "Февраль": false, "Март": false, "Апрель": false, "Май": false, "Июнь": false,
    "Июль": false, "Август": false, "Сентябрь": false, "Октябрь": false, "Ноябрь": false, "Декабрь": false
  },

  // Объект для годов
  years: {}
});

let name = ref('lol i hate myself');
let male = ref(false);
onBeforeMount(() => {
  let currentYear = new Date().getFullYear();
  for (let year = 1950; year <= currentYear; year++) {
    switch (year) {
      case 1950:
        days.value.years[year + 'Г.'] = true;
        break;
      default:
        days.value.years[year + 'Г.'] = false;
    }

  }
})


</script>

<template>
  <div class="container">
    <div class="wrapper">
      <div class="calc">
        <div class="left">
          <div class="date">
            <div class="row">
              <matrix-select-small name="Число" v-model="days.daysOfMonth"/>
              <matrix-select-small name="Месяц" v-model="days.months"/>
              <matrix-select-small name="Год" v-model="days.years"/>
            </div>
            <div class="btn">
              <span>Рассчитать</span>
            </div>
          </div>
          <div class="matrix">
            <matrix-diagram/>
          </div>
        </div>
        <div class="right">
          <div class="table">
            <matrix-table/>
          </div>
          <div class="harmony">

          </div>
        </div>
      </div>
      <div class="fantasy">
        <matrix-texts/>
        <matrix-texts/>
        <matrix-texts/>
        <matrix-texts/>
        <matrix-texts/>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@keyframes pulse {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.2);
  }

  100% {
    transform: scale(1);
  }
}

.wrapper {
  width: 1140px;
  margin: 0 auto;
  padding-top: 60px;
}

.container {
  background:linear-gradient(rgba(255,255,255,0.8), rgba(255,255,255,0.8)), url("/img/bg.jpg");
}

.calc {
  display: flex;
  gap: 30px;
  .left {
    width: 50%;
    .date {
      //width: 380px;
      background: white;
      border-radius: 15px;
      box-shadow: 0 0 40px rgba(198, 198, 198, 0.25);
      padding: 30px;
      .row {
        display: flex;
        justify-content: space-around;
      }
      .btn {
        padding: 20px 40px 20px 40px;
        background-image: linear-gradient(180deg, #4CBB11 0%, #047C3C 100%);
        width: max-content;
        border-radius: 20px;
        color: #fff;
        font-family: Roboto, sans-serif;
        cursor: pointer;
        margin: 30px auto 0 auto;
        &:hover {
          animation: pulse 1s linear infinite;
        }
      }
    }
    .matrix {
      margin-top: 40px;
      //width: 380px;
      padding: 30px;
      background: white;
      border-radius: 15px;
      box-shadow: 0 0 40px rgba(198, 198, 198, 0.25);

    }
  }
  .right {
    width: 50%;

    .table {
      //width: 380px;
      padding: 30px;
      background: white;
      border-radius: 15px;
      box-shadow: 0 0 40px rgba(198, 198, 198, 0.25);
    }
  }
}
</style>