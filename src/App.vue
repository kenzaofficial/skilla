<template>
  <default-layout>
    <template v-slot:header>
      <v-header></v-header>
    </template>
    <template v-slot:aside>
      <v-aside></v-aside>
    </template>
    <template v-slot:main>
      <div class="upper-row">
        <div class="balance">
          Баланс:<span class="balance__value">272 ₽</span>
          <button class="balance__button">
            <img src="@/assets/balance-btn.svg" alt="plus" />
          </button>
        </div>
        <button type="button" class="calendar-button">
          <img src="@/assets/calendar.svg" />3дня
        </button>
      </div>
      <div class="filter-row">
        <input class="filter-row__search" placeholder="Поиск по звонкам" />
        <ul class="filter-row__list">
          <li class="filter-row__item">Все типы</li>
          <li class="filter-row__item">Все сотрудники</li>
          <li class="filter-row__item">Все звонки</li>
          <li class="filter-row__item">Все источники</li>
          <li class="filter-row__item">Все оценки</li>
          <li class="filter-row__item">Все ошибки</li>
        </ul>
      </div>
    </template>
    <template v-slot:footer></template>
  </default-layout>
</template>

<script>
import VAside from './components/v-aside.vue';
import defaultLayout from './components/default-layout.vue';
import VHeader from './components/v-header.vue';

export default {
  name: 'App',
  components: {
    defaultLayout,
    VAside,
    VHeader,
  },
};
</script>

<style>
body {
  margin: 0;
}

#app {
  display: grid;
  grid-template-columns: 240px auto;
  grid-template-rows: auto 1fr;
}

main {
  padding: 20px 0;
  background-color: #f1f4f9;
  grid-row: 2/2;
  grid-column: 2/-1;
}

.upper-row {
  display: flex;
  column-gap: 50px;
  margin-bottom: 20px;
}

.balance {
  box-sizing: border-box;
  background-color: #fff;
  border-radius: 48px;
  padding: 9px 12px;
  max-width: 145px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: auto;
  color: #899cb1;
}

.balance__value {
  color: #000;
}

.balance__button {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 5px;
  width: 24px;
  height: 24px;
  border: none;
  background-color: transparent;
  border-radius: 50%;
  transition: 0.3s;
  cursor: pointer;
}

.balance__button:hover {
  transform: scale(1.1);
}

.calendar-button {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 20px;
  border: none;
  column-gap: 10px;
  cursor: pointer;
  transition: 0.8s;
  border-radius: 48px;
  color: blue;
}

.calendar-button:hover {
  background-color: #333;
  color: #fff;
}

.calendar-button:before,
.calendar-button::after {
  display: inline-block;
  content: '';
  width: 24px;
  height: 24px;
}

.calendar-button:before {
  background: url(@/assets/arrowback.svg) no-repeat center;
}

.calendar-button:after {
  background: url(@/assets/arrowforward.svg) no-repeat center;
}

.filter-row {
  display: flex;
}

.filter-row__search {
  padding-left: 30px;
  background: url(@/assets/search.svg) no-repeat center left;
  border: none;
  color: #5e7793;
}

.filter-row__list {
  margin: 0;
  padding: 0;
  display: flex;
  margin-left: auto;
  list-style: none;
  column-gap: 30px;
}

.filter-row__item {
  padding: 10px 20px 10px 10px;
  background: url(@/assets/dropdown.svg) no-repeat center right 3px;
  cursor: pointer;
  border-radius: 48px;
  color: #5e7793;
  transition: 0.3s;
}

.filter-row__item:hover {
  background-color: #333;
  color: #fff;
}
</style>
