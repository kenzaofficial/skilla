<template>
  <div class="table-calls-wrapper">
    <table class="table-calls">
      <thead class="table-calls__header">
        <tr class="table-calls__header-row">
          <th>Тип</th>
          <th>Время</th>
          <th>Сотрудник</th>
          <th>Звонок</th>
          <th>Источник</th>
          <th>Оценка</th>
          <th>Длительность</th>
        </tr>
      </thead>
      <tbody class="table-calls__body">
        <tr
          class="table-calls__body-row"
          v-for="(item, index) in list"
          :key="index"
        >
          <td v-if="item.in_out === 1 && item.status == 'Дозвонился'">
            <img src="@/assets/svg/incoming.svg" />
          </td>
          <td v-if="item.in_out === 0 && item.status == 'Дозвонился'">
            <img src="@/assets/svg/outcoming.svg" />
          </td>
          <td v-if="item.status === 'Не дозвонился'">
            <img src="@/assets/svg/missedcoming.svg" />
          </td>
          <td>
            <span>
              {{ formattedTime[index] }}
            </span>
          </td>
          <td class="table-calls__avatar">
            <img :src="item.person_avatar" />
          </td>
          <td class="table-calls__phone-number">
            <a :href="'tel:' + item.partner_data.phone">{{
              formattedTelNumber[index]
            }}</a>
          </td>
          <td>
            <span>{{ item.partner_data.name }}</span>
          </td>
          <td v-if="item.time >= minuteDuration">
            <div class="table-calls__grade">
              <span
                class="table-calls__grade-marker table-calls__grade-marker--best"
              ></span>
              <span
                class="table-calls__grade-text table-calls__grade-text--best"
                >Отлично</span
              >
            </div>
          </td>
          <td v-else-if="item.time < minuteDuration && item.time > 0">
            <div class="table-calls__grade">
              <span
                class="table-calls__grade-marker table-calls__grade-marker--good"
              ></span>
              <span
                class="table-calls__grade-text table-calls__grade-text--good"
                >Хорошо</span
              >
            </div>
          </td>
          <td v-else-if="item.time === 0">
            <div class="table-calls__grade">
              <span
                class="table-calls__grade-marker table-calls__grade-marker--bad"
              ></span>
              <span class="table-calls__grade-text table-calls__grade-text--bad"
                >Плохо</span
              >
            </div>
          </td>
          <td>
            <span> {{ formattedDuration[index] }}</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import dayjs from 'dayjs';
export default {
  data: () => ({
    minuteDuration: 59,
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
        })
        .catch((error) => console.error(error));
    },
  },
  computed: {
    formattedTime() {
      return this.list.map((item) => dayjs(item.date).format('HH:mm'));
    },
    formattedDuration() {
      return this.list.map((item) => {
        const minutes = Math.floor(item.time / 60);
        const seconds = item.time % 60;
        const timeResult = seconds < 10 ? `0${seconds}` : seconds;
        return `${minutes}:${timeResult}`;
      });
    },
    formattedTelNumber() {
      return this.list.map((item) =>
        item.partner_data.phone.replace(
          /^(\d{1})(\d{3})(\d{3})(\d{2})(\d{2})$/,
          '+$1 ($2) $3-$4-$5'
        )
      );
    },
  },
  mounted() {
    this.getList();
  },
};
</script>
<style>
.table-calls-wrapper {
  padding: 0 20px;
  background-color: #fff;
  border-radius: 8px;
}

.table-calls {
  width: 100%;
  border-spacing: 0 0;
  border-collapse: collapse;
}

.table-calls__header {
  font-family: 'SF Pro';
  font-size: 14px;
  color: #899cb1;
  height: 50px;
  border-bottom: 1px solid #eff0fa;
}

.table-calls__body-row {
  height: 60px;
  border-bottom: 1px solid #eff0fa;
}

.table-calls__header-row th {
  font-weight: 400;
}

.table-calls__avatar img {
  width: 32px;
  height: 32px;
  border-radius: 50%;
}

/* ---------------------------------default grade starts--------------------------- */
.table-calls__grade-marker,
.table-calls__grade-marker::before,
.table-calls__grade-marker::after {
  width: 8px;
  height: 8px;
  border-radius: 50px;
  background-color: #000;
}

.table-calls__grade-marker {
  display: inline-block;
  position: relative;
  margin-right: 18px;
}

.table-calls__grade-marker::before,
.table-calls__grade-marker::after {
  position: absolute;
  content: '';
  top: 0;
}

.table-calls__grade-marker::before {
  left: -10px;
}

.table-calls__grade-marker::after {
  left: 10px;
}

.table-calls__grade-text {
  display: inline-block;
  padding: 5px 8px;
  font-size: 14px;
  line-height: 14px;
  border-radius: 4px;
  background-color: brown;
  border: 1px solid #000;
}

/* --------------------default grade ends---------------- */

/* --------------------best grade starts--------------- */
.table-calls__grade-marker--best,
.table-calls__grade-marker--best::before,
.table-calls__grade-marker--best::after {
  background-color: #28a879;
}

.table-calls__grade-marker--best::before {
  left: -10px;
}

.table-calls__grade-marker--best::after {
  left: 10px;
}

.table-calls__grade-text--best {
  background-color: #dbf8ef;
  border-color: #28a879;
}

/* --------------------best grade ends---------------- */

/* --------------------good grade starts---------------- */
.table-calls__grade-marker--good,
.table-calls__grade-marker--good::before {
  background-color: #adbfdf;
}

.table-calls__grade-marker--good::after {
  background-color: transparent;
}

.table-calls__grade-text--good {
  background-color: #d8e4fe;
  border-color: #adbfdf;
}

/* --------------------good grade ends---------------- */

/* --------------------bad grade starts---------------- */

.table-calls__grade-marker--bad::before {
  background-color: #ea1a4f;
}

.table-calls__grade-marker--bad,
.table-calls__grade-marker--bad::after {
  background-color: transparent;
}

.table-calls__grade-text--bad {
  background-color: #fee9ef;
  border-color: #ea1a4f;
}

/* --------------------bad grade ends---------------- */

.table-calls__header-row th:not(:last-child) {
  padding-right: 10px;
  text-align: left;
}

.table-calls__header-row th:last-child,
td:last-child {
  text-align: right;
}

.table-calls__phone-number a {
  color: #000;
  text-decoration: none;
}
</style>
