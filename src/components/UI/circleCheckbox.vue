<template>
      <input type="checkbox" class="custom-checkbox" id="happy" name="happy" value="yes">
</template>

<style scoped>
input {
  display: inline-block;
  --max-width: 28px;
  height: var(--max-width);
  width: var(--max-width);
  border-radius: 50%;
    vertical-align: middle;
    border: 2px solid #ddd;
    appearance: none;
    -webkit-appearance: none;
    outline: none;
    cursor: pointer;
}
input:checked{
  background-color: var(--bg-color-pink);
}
</style>
