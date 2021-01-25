<template>
  <div class="home">
   <v-card class="overflow-hidden">
    <Header/>
   


    <v-sheet
      id="scrolling-techniques-5"
      class="overflow-y-auto"
      style="height:100vh;"
    >
      <v-container style="height: 0px; " ></v-container>
      <br><br><br>
      <br><br><br>
      <div style="padding:10px;">
 <v-card
    class="mx-auto"
    max-width="600"
  >
  
    <v-card-actions>
      <v-btn
        text
        color="deep-purple accent-4"
        @click="$router.go(-1)" 
      >
       <v-icon >
            mdi-arrow-left
          </v-icon>
      </v-btn>
        <v-btn
        text
        color="deep-purple accent-4"
      >
       Nigeria
      </v-btn>
    </v-card-actions>
  </v-card>
<br>
<br>
<div style="max-width:600px;" class="mx-auto">
 <h2 class="font-weight-bold"> States</h2>
</div>
<br>



<v-card
    class="mx-auto"
    max-width="600"
  >
   <v-list-item three-line
    v-for="(nigeria, i) in nigeria"
    :key="i"
   >
      <v-list-item-content>
        
        <v-list-item-title class="font-weight-bold" color="primary">
        
          &nbsp;&nbsp;&nbsp;{{nigeria.region}}</v-list-item-title>
          <div style="margin-left:15px;">
        <v-list-item-subtitle style="padding:0px;">
     <span style="color:black; font-size:40px;">-</span>  <b>{{ Number(nigeria.labConfirmedCases).toLocaleString()}}</b> - Total cases
        </v-list-item-subtitle>
          <v-list-item-subtitle style="padding:0px;">
     <span style="color:green; font-size:40px;">-</span>  <b>{{ Number(nigeria.onAdmissionCases).toLocaleString()}}</b> - Current cases
        </v-list-item-subtitle>
        <v-list-item-subtitle style="padding:0px;">
    <span style="color:blue; font-size:40px;">-</span>  <b>{{ Number(nigeria.discharged).toLocaleString()}}</b> - Discharged
        </v-list-item-subtitle>
        <v-list-item-subtitle style="padding:0px;">
    <span style="color:red; font-size:40px;">-</span>  <b>{{ Number(nigeria.deaths).toLocaleString()}}</b> - Deaths
        </v-list-item-subtitle>
          </div>
      </v-list-item-content>
    </v-list-item>
   </v-card>

      </div>
  <br><br>
  
  <Footer/>


         </v-sheet>
  </v-card>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'


export default {
  name: 'Home',
  // data: () => ({
  //     drawer: false,
  //     group: null,
  //   }),

   metaInfo() {
        return { 
            title: "Nigeria - GoDemic",
            meta: [
                { name: 'description', content:  'Get up to date information of the coronavirus pandemic on GoDemic'},
                { property: 'og:title', content: "Nigeria - GoDemic"},
                { property: 'og:site_name', content: 'GoDemic'},
                {property: 'og:type', content: 'website'},    
                {name: 'robots', content: 'index,follow'} 
            ]
        }
    },

    components: {
    Header,
    Footer
  },
  data () {
    return {
      nigeria:{},
    }
  },
 

   methods: {

   getNigeria () {
        fetch("https://api.apify.com/v2/key-value-stores/Eb694wt67UxjdSGbc/records/LATEST?disableRedirect=true")
          .then(res => {
            return res.json();
          }).then(this.setNigeria);
    },
    setNigeria (results) {
      this.nigeria = results.regions;
    },

  },

   mounted(){
    this.getNigeria()
  }
}
</script>
