<!-- eslint-disable prettier/prettier -->
<template>
  <div class="filter-row">
    <input class="filter-row__search" placeholder="Поиск по звонкам" />
    <ul class="filter-row__list">
      <li v-for="(item, index) in filtres" :key="index" class="filter-row__item">
        {{ item.description }}</li>
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
          description: 'Все сотрудники',
        },
        {
          description: 'Все звонки',
        },
        {
          description: 'Все источники',
        },
        {
          description: 'Все оценки',
        },
        {
          description: 'Все ошибки',
        },
      ],
    };
  },
};
</script>

<style>
.filter-row {
  display: flex;
  margin-bottom: 20px;
}

.filter-row__search {
  padding-left: 30px;
  background: url(@/assets/search.svg) no-repeat center left 5px;
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
  border-radius: 8px;
  color: #5e7793;
  transition: 0.3s;
}

.filter-row__item:hover {
  background-color: #333;
  color: #fff;
}
</style>
