<script setup lang="ts">
import {ref, onBeforeMount} from 'vue'
import MatrixSelect from "~/component/matrixSelect.vue";

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
  <div class="demo">
    <div class="left">
      <h1>
        Рассчитать <span class="font-green">Матрицу судьбы</span> онлайн с расшифровкой
      </h1>
      <div class="birthday-form">
        <span class="birthday-form__header">
          Введите дату рождения
        </span>
        <div class="row">
          <matrix-select name="Число" v-model="days.daysOfMonth"/>
          <matrix-select name="Месяц" v-model="days.months"/>
          <matrix-select name="Год" v-model="days.years"/>
        </div>
        <div class="row personal-data">
          <input type="text" v-model="name" placeholder="Ваше имя*">
          <div class="sex">
            <div class="btn" @click="male = false" :class="male?'':'active'">
              <span>Ж</span>
            </div>
            <div class="btn" @click="male = true" :class="male?'active':''">
              <span>М</span>
            </div>
          </div>
        </div>
        <div class="submit">
          <span>Рассчитать</span>
        </div>
      </div>
    </div>
    <div class="right">
      <img src="/img/matrixImg.png" height="1013" width="1024"/>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.row {
  display: flex;
  justify-content: space-between;
  gap: 5px;
}

.demo {
  display: flex;
  gap: 20px;

  .left {
    padding-top: 150px;
    font-family: Roboto, sans-serif;

    h1 {
      font-size: 38px;
      font-weight: 500;
      color: #6F6F6F;
      line-height: 68px;
      margin-bottom: 65px;

      span {
        color: #1AA217;
      }
    }

    .birthday-form {
      display: flex;
      flex-direction: column;

      &__header {
        font-weight: bold;
        font-size: 24px;
        text-align: center;
        margin-bottom: 20px;
      }
    }

    .personal-data {
      margin-top: 10px;

      input {
        padding: 10px 30px;
        border: 1px solid #6f6f6f;
        border-radius: 15px;
        font-size: 20px;
        width: 100%;
      }

      .sex {
        border: 1px solid #6f6f6f;
        border-radius: 15px;
        display: flex;
        line-height: 0;
        align-items: center;
        cursor: pointer;
        user-select: none;

        span {
          padding: 20px;
        }

        .btn {
          height: 100%;
          display: flex;

          &:first-child {
            border-radius: 14px 0 0 14px;
          }

          &:last-child {
            border-left: 1px solid #6f6f6f;
            border-radius: 0 14px 14px 0;
          }
        }

        .active {
          background: #1AA217;
          color: white;
        }
      }
    }

    .submit {
      margin-top: 20px;
      margin-left: 60px;
      width: 86px;
      font-family: "Montserrat", sans-serif;
      font-weight: 500;
      background-color: #1AA217;
      border-radius: 18px 18px 18px 18px;
      padding: 15px 60px 15px 60px;
      font-size: 15px;
      color: white;
      cursor: pointer;
      transition: 0.2s linear;
      &:hover {
        transform: scale(1.1);
      }
    }
  }

  .right {
    img {
      width: 100%;
      height: auto;
    }
  }
}
</style>