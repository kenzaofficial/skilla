<template>
  <img src="../assets/logo.svg" width="109" height="28" class="logo" />
  <ul class="aside__list list">
    <li v-for="(item, index) in nav" :key="index" class="list__item">
      <img :src="item.imgPath" class="list__img" />
      <span class="list__text"> {{ item.description }}</span>
    </li>
  </ul>
</template>

<script>
document.addEventListener('DOMContentLoaded', () => {
  const listItems = document.querySelectorAll('.list__item');
  console.log(listItems);
  listItems.forEach(function (listItem) {
    listItem.addEventListener('click', function () {
      listItems.forEach(function (listItem) {
        listItem.classList.remove('list__item--active');
      });
      listItem.classList.toggle('list__item--active');
    });
  });
});
export default {
  data() {
    return {
      nav: [
        {
          imgPath: require('@/assets/list/icon_01.svg'),
          description: 'Итоги',
        },
        {
          imgPath: require('@/assets/list/icon_02.svg'),
          description: 'Заказы',
        },
        {
          imgPath: require('@/assets/list/icon_03.svg'),
          description: 'Сообщения',
        },
        {
          imgPath: require('@/assets/list/icon_04.svg'),
          description: 'Звонки',
        },
        {
          imgPath: require('@/assets/list/icon_05.svg'),
          description: 'Контрагенты',
        },
        {
          imgPath: require('@/assets/list/icon_06.svg'),
          description: 'Документы',
        },
        {
          imgPath: require('@/assets/list/icon_07.svg'),
          description: 'Исполнители',
        },
        {
          imgPath: require('@/assets/list/icon_08.svg'),
          description: 'Отчеты',
        },
        {
          imgPath: require('@/assets/list/icon_09.svg'),
          description: 'База знаний',
        },
        {
          imgPath: require('@/assets/list/icon_10.svg'),
          description: 'Настройки',
        },
      ],
    };
  },
};
</script>

<style>
.aside {
  padding: 20px 0;
  max-width: 240px;
  width: 100%;
  background-color: #091336;
  order: -1;
}

.logo {
  padding: 0 14px;
}

.list {
  height: 100vh;
  margin: 10px 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  list-style-type: none;
}

.list__item {
  box-sizing: border-box;
  padding: 14px;
  display: flex;
  align-items: center;
  column-gap: 12px;
  border-left: 5px solid transparent;
  cursor: pointer;
  transition: 0.3s;
}

.list__item:hover {
  background-color: #641717;
}

.list__item--active {
  position: relative;
  border-color: #ffd500;
  background-color: rgba(216, 228, 251, 0.32);
}

.list__item--active::after {
  position: absolute;
  content: '';
  top: 50%;
  right: 15px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #ffd500;
  box-shadow: 0px 3px 8px 0px #edda0180;
  transform: translateY(-50%);
}

.list__item--active .list__text {
  color: #fff;
}

.list__text {
  color: rgba(255, 255, 255, 0.6);
}
</style>
