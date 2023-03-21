<template>
  <div class="balance">
    Баланс:<span class="balance__value">272 ₽</span>
    <button class="balance__button">
      <img src="@/assets/balance-btn.svg" alt="plus" />
    </button>
  </div>
</template>

<script>
export default {};
</script>

<style>
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
</style>
