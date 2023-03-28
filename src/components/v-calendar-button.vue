<template>
  <button type="button" class="calendar-button">
    <img src="@/assets/svg/calendar.svg" />3дня
  </button>
</template>

<script>
export default {};
</script>

<style>
.calendar-button {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 20px;
  border: none;
  column-gap: 10px;
  cursor: pointer;
  background-color: transparent;
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
  background: url(@/assets/svg/arrowback.svg) no-repeat center;
}

.calendar-button:after {
  background: url(@/assets/svg/arrowforward.svg) no-repeat center;
}
</style>
