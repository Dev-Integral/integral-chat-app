<template>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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
    background-color: #f3f6fb;
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
