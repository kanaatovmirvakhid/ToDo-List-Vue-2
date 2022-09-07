<template>
  <div class="openButton" @click="$emit('returnTrue')"></div>
</template>

<style scoped>
.openButton{
    position: fixed;
    background-color: var(--bg-color-pink);
    border-radius: 50%;
    height: 50px;
    width: 50px;
}
.openButton::after{
    content: "";
    background-color: white;
    position: absolute;
    height: 5%;
    width: 50%;
    top: 48%;
    left: 26%;
}
.openButton::before{
    content: "";
    background-color: white;
    position: absolute;
    height: 50%;
    width: 5%;
    left: 48%;
    top: 27%;
}
</style>
