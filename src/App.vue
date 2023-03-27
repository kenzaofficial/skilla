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
        <v-balance></v-balance>
        <v-calendar-button></v-calendar-button>
      </div>
      <v-filter-row></v-filter-row>
      <table class="table">
        <thead class="table__header">
          <tr class="table__header-row">
            <th>Тип</th>
            <th>Время</th>
            <th>Сотрудник</th>
            <th>Звонок</th>
            <th>Источник</th>
            <th>Оценка</th>
            <th>Длительность</th>
          </tr>
        </thead>
        <tbody class="table__body">
          <tr v-for="(item, index) in list" :key="index">
            <td v-if="item.in_out === 1">
              <img src="@/assets/svg/incoming.svg" />
            </td>
            <td v-if="item.in_out === 0">
              <img src="@/assets/svg/outcoming.svg" />
            </td>
            <td v-if="item.in_out === 2">
              <img src="@/assets/svg/missedcoming.svg" />
            </td>
            <td>
              <span>
                {{ item.date }}
              </span>
            </td>
            <td class="table__avatar">
              <img :src="item.person_avatar" />
            </td>
            <td>
              <a :href="'tel:' + item.partner_data.phone">{{
                item.partner_data.phone
              }}</a>
            </td>
            <td>
              <span>{{ item.partner_data.name }}</span>
            </td>
            <td>
              <span>{{ item.is_skilla }}</span>
            </td>
            <td>
              <span>{{ item.time }}</span>
            </td>
          </tr>
        </tbody>
      </table>
    </template>
    <template v-slot:footer></template>
  </default-layout>
</template>

<script>
import VAside from './components/v-aside.vue';
import defaultLayout from './components/default-layout.vue';
import VHeader from './components/v-header.vue';
import VFilterRow from './components/v-filter-row.vue';
import VBalance from './components/v-balance.vue';
import VCalendarButton from './components/v-calendar-button.vue';

export default {
  name: 'App',
  components: {
    defaultLayout,
    VAside,
    VHeader,
    VFilterRow,
    VBalance,
    VCalendarButton,
  },
  data: () => ({
    token: 'Bearer testtoken',
    list: [],
    options: {},
  }),
  methods: {
    getList() {
      this.options = {
        method: 'POST',
        headers: {
          Authorization: this.token,
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({}),
      };
      fetch('https://api.skilla.ru/mango/getList', this.options)
        .then((response) => response.json())
        .then((data) => {
          this.list = data.results;
          console.log(this.list);
        })
        .catch((error) => console.error(error));
    },
    isStatusCall(status) {
      if (status === 0) {
        return true;
      } else {
        return false;
      }
    },
  },
  mounted() {
    this.getList();
  },
};
</script>

<style>
body {
  margin: 0;
}

.app {
  height: 100vh;
  display: grid;
  grid-template-columns: 240px auto;
  grid-template-rows: auto 1fr;
}

.main {
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

.table {
  width: 100%;
  border-spacing: 0 0;
}

.table__header {
  font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
  font-size: 14px;
  color: #899cb1;
  height: 50px;
  border-bottom: 1px solid gray;
  background-color: #0f4914;
}

.table__body tr {
  height: 60px;
  border-bottom: 1px solid gray;
}

.table__body tr:nth-child(odd) {
  background-color: rgb(175, 236, 140);
}

.table__body tr:nth-child(even) {
  background-color: rgb(156, 200, 236);
}

.table__body td:first-child,
.table__header-row th:first-child {
  padding-left: 20px;
}

.table__body td:last-child,
.table__header-row th:last-child {
  padding-right: 20px;
}

.table__header-row th {
  font-weight: 400;
}

.table__avatar img {
  width: 32px;
  height: 32px;
  border-radius: 50%;
}

.table__header-row th:not(:last-child) {
  text-align: left;
}

.table__header-row th:last-child,
td:last-child {
  text-align: right;
}
</style>
