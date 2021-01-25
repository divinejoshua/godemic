<template>
  <v-app class="LayoutDefault">
  <router-view></router-view>
    <v-main>
    </v-main>
  </v-app>
</template>
<style> *{ text-transform: none !important; } 
     .trend-tag{
      color: #007bff;
      text-decoration: none;
      font-size: 13px;
    }
</style>
<script>
export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
