<template>
  <router-view></router-view>
</template>

<style>
@import url("https://fonts.googleapis.com/css?family=Poppins");
#app {
  font-family: 'Poppins', Arial, sans-serif;
  color: #2c3e50;
  background: #fff;

}
body{
  margin: 20px;
}
p, h1, h2,h3,h4,h5,h6{
  margin: 0;
}
::-webkit-scrollbar {
    width: 4px;
    height: 1px  !important;
    border-radius: 3rem !important;
}


::-webkit-scrollbar-track {
  border: 1px solid #e0e1e4;
    /* background-color: #f3f3f3; */
}

::-webkit-scrollbar-thumb {
    background-color: #D3E5F5;
    cursor: pointer;
}

::-webkit-scrollbar-thumb:hover {
    background-color: #2c3e50;
    cursor: pointer;
}

</style>
