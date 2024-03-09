<script setup lang="ts">

</script>

<template>
    <div class="header">
        <div class="icon">
            <img src="/img/матрица%20судьбы%20лого3%20(2).png"/>
        </div>
        <div class="wrapper">
            <div class="navbar">
                <div class="home">
                    <NuxtLink to="/">
                        <svg width="23" height="23" viewBox="0 0 25 22" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M4.5 10.5V21H10C10 21 10 18.5 10 14.5C10 10.5 15.5 10.5 15.5 14.5C15.5 18.5 15.5 21 15.5 21H21V10.5M23.5 9.5L13 2L1.5 9.5"
                                  stroke="white" stroke-width="2"/>
                        </svg>
                    </NuxtLink>
                </div>
                <ul>
                    <li>
                        Матрица судьбы
                    </li>
                    <li>
                        Совместимость
                    </li>
                    <li>
                        Детская матрица
                    </li>
                    <li>
                        Дополнительные расчеты
                    </li>
                    <li>
                        Интересное
                    </li>
                    <li>
                        Отзывы
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  position: fixed;
  top: 0;
  left: 0;
  padding: 10px 0;
  background: #1AA217;
  height: 60px;
  width: 100%;

  .icon {
    margin: 0 0 0 166px;

    img {
      height: 60px;
    }
  }

  .wrapper {
    width: 1140px;
    margin: 0 auto;
    display: flex;
    align-items: center;

    .navbar {
      display: flex;
      align-items: center;

      .home {
        margin-right: 15px;
        transition: 0.4s linear;

        &:hover {
          transform: scale(1.1);
        }
      }

      ul {
        display: flex;
        gap: 30px;
        color: #fff;
        font-family: Inter, sans-serif;
      }

      li {
        cursor: pointer;

        &::marker {
          content: none;
        }
      }
    }
  }
}
</style>