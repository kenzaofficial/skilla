<!-- eslint-disable prettier/prettier -->
<template>
  <span class="header__date">Среда, 13 окт</span>
  <ul class="header__progress-list progress-list">
    <li class="progress-list__item">
      <p class="progress-list__description">Новые звонки <span style="color:#28A879" class="progress-list__value">20 из
          30шт</span></p>
      <div class="progress-list__bar progress-list__bar--first"></div>
    </li>
    <li class="progress-list__item">
      <p class="progress-list__description">Качество разговоров <span style="color:#FFD500"
          class="progress-list__value">40%</span></p>
      <div class="progress-list__bar progress-list__bar--second"></div>
    </li>
    <li class="progress-list__item">
      <p class="progress-list__description">Конверсия в заказ <span style="color:#EA1A4F"
          class="progress-list__value">67%</span></p>
      <div class="progress-list__bar progress-list__bar--third"></div>
    </li>
  </ul>
  <input class="header__input" type="name" placeholder="ИП Сидорова Александра Михайловна">
  <button type="button" class="header__dropdown">
    <img src="@/assets/svg/dropdown.svg">
  </button>
  <img class="header__avatar" src="@/assets/img/avatar.jpg">
  <button type="button" class="header__dropdown">
    <img src="@/assets/svg/dropdown.svg">
  </button>
</template>

<script>
export default {};
</script>

<style>
.header {
  padding: 15px 0;
  box-shadow: 0px 4px 5px 0px #e9edf3;
  align-self: flex-start;
}

.header__container {
  display: flex;
  align-items: center;
}

.header__date {
  font-size: 12px;
  color: #899cb1;
  margin-right: 75px;
}

.progress-list {
  display: flex;
  margin: 0;
  padding: 0;
  column-gap: 30px;
  margin-right: 20px;
  list-style: none;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 12px;
  color: #122945;
}

.progress-list__description {
  margin: 0 0 10px 0;
}

.progress-list__bar {
  position: relative;
  height: 6px;
  border-radius: 12px;
  background-color: #dee6f5;
}

.progress-list__bar::before {
  position: absolute;
  content: '';
  height: 100%;
  top: 0;
  left: 0;
  width: 40%;
  border-radius: 12px;
}

.progress-list__bar--first::before {
  background-color: #28a879;
}

.progress-list__bar--second::before {
  background-color: #ffd500;
}

.progress-list__bar--third::before {
  background-color: #ea1a4f;
}

.header__input {
  display: inline-block;
  border: none;
  max-width: 250px;
  width: 100%;
  padding-left: 40px;
  background-image: url(@/assets/svg/search.svg);
  background-repeat: no-repeat;
}

.header__dropdown {
  width: 24px;
  height: 24px;
  padding: 0;
  cursor: pointer;
  border: none;
  background-color: transparent;
}

.header__avatar {
  margin-left: auto;
  max-width: 40px;
  height: auto;
}
</style>
