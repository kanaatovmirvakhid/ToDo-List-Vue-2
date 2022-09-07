<template>
  <div class="closeButton"></div>
</template>

<style scoped>
.closeButton{
    position: absolute;
    background-color: red;
    border-radius: 50%;
    height: 25px;
    width: 25px;
}
.closeButton::after{
    content: "";
    background-color: white;
    position: absolute;
    height: 10%;
    width: 50%;
    top: 40%;
    left: 24%;
    transform: rotate(135deg);
}
.closeButton::before{
    content: "";
    background-color: white;
    position: absolute;
    height: 10%;
    width: 50%;
    top: 40%;
    left: 24%;
    transform: rotate(45deg);
}
</style>
