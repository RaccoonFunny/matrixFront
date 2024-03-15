<script setup lang="ts">

</script>

<template>
  <div class="section-with-diagram__col-with-table">
    <h3 class="table-header">Персональный расчёт</h3>
    <p class="table-label">Карта здорвья</p>
    <table class="section-with-diagram__table table health-table js-health-table">
      <thead>
      <tr>
        <th scope="col">Название Чакры</th>
        <th scope="col">Физика</th>
        <th scope="col">Энергия</th>
        <th scope="col">Эмоции</th>
      </tr>
      </thead>
      <tbody>
      <tr class="-purple-row" data-row-number="1">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">7. Сахасрара</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="a">11</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="b">11</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="l">22</td>
      </tr>
      <tr class="-blue-row" data-row-number="2">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">6. Аджна</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="a2">11</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="b2">11</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="l1">22</td>
      </tr>
      <tr class="-cyan-row" data-row-number="3">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">5. Вишудха</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="a1">18</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="b1">18</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="l2">9</td>
      </tr>
      <tr class="-green-row" data-row-number="4">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">4. Анахата</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="a3">7</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="b3">7</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="l3">14</td>
      </tr>
      <tr class="-yellow-row" data-row-number="5">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">3. Манипура</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="e">7</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="e">7</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="l4">14</td>
      </tr>
      <tr class="-orange-row" data-row-number="6">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">2. Свадхистана</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="c1">11</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="d1">15</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="l5">8</td>
      </tr>
      <tr class="-red-row" data-row-number="7">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">1. Муладхара</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="c">4</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="d">8</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="l6">12</td>
      </tr>
      <tr class="-gray-row" data-row-number="8">

        <td>
          <div class="h5 table-title-with-prompt">
            <span class="table-title-with-prompt__text">Итог</span>
          </div>
        </td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="d3">15</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="c3">14</td>
        <td class="js-personal-calculation-item -active" data-personal-calculation-position="e3">2</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped lang="scss">
.table-header {
  font-family: Montserrat, sans-serif;
  font-weight: bold;
  color: black;
  margin-bottom: 10px;
  font-size: 12px;
}

.table-label {
  font-family: Montserrat, sans-serif;
  color: #af9e9b;
  margin-bottom: 10px;
  font-size: 9px;
}
</style>