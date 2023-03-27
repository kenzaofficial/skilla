<template>
  <nav class="main-nav">
    <ul class="main-nav-list">
      <li
        v-for="(item, index) in nav"
        :key="index"
        v-on:click="setActive(index)"
        :class="{ 'main-nav-list__item--active': activeIndex === index }"
        class="main-nav-list__item"
      >
        <img :src="item.imgPath" class="main-nav-list__img" />
        <span class="main-nav-list__text"> {{ item.description }}</span>
      </li>
    </ul>
  </nav>
</template>

<script>
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
      activeIndex: null,
    };
  },
  methods: {
    setActive(index) {
      this.activeIndex = index;
    },
  },
};
</script>

<style>
.main-nav-list {
  margin: 10px 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
  list-style-type: none;
}

.main-nav-list__item {
  box-sizing: border-box;
  padding: 14px;
  display: flex;
  align-items: center;
  column-gap: 12px;
  border-left: 5px solid transparent;
  cursor: pointer;
  transition: 0.3s;
}

.main-nav-list__item:hover {
  background-color: #916868;
}

.main-nav-list__item--active {
  position: relative;
  border-color: #ffd500;
  background-color: rgba(216, 228, 251, 0.32);
}

.main-nav-list__item--active::after {
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

.main-nav-list__item--active .main-nav-list__text {
  color: #fff;
}

.main-nav-list__text {
  color: rgba(255, 255, 255, 0.6);
}
</style>
