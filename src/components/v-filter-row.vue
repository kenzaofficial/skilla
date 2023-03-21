<!-- eslint-disable prettier/prettier -->
<template>
  <div class="filter-row">
    <input class="filter-row__search" placeholder="Поиск по звонкам" />
    <ul class="filter-row__list">
      <li v-for="(item, index) in filtres" :key="index" class="filter-row__item">
        {{ item.description }}</li>
    <!-- <li class="filter-row__item">Все типы</li>
      <li class="filter-row__item">Все сотрудники</li>
      <li class="filter-row__item">Все звонки</li>
      <li class="filter-row__item">Все источники</li>
      <li class="filter-row__item">Все оценки</li>
          <li class="filter-row__item">Все ошибки</li> -->
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filtres: [
        {
          description: 'Все типы',
        },
        {
          description: 'Все типы',
        },
        {
          description: 'Все типы',
        },
        {
          description: 'Все типы',
        },
        {
          description: 'Все типы',
        },
        {
          description: 'Все типы',
        },
      ],
    };
  },
};
</script>

<style>
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
