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
    <v-card-text>
      <p class="display-3 text--primary">
        Nigeria
      </p>
      <v-divider></v-divider>
      <br>
        <v-list-item>
        <v-list-item-icon>
          <v-icon color="green">
            mdi-circle
          </v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title class="display-1 text--primary">{{ Number(nigeria.infected).toLocaleString()}}</v-list-item-title>
          <v-list-item-subtitle>  
          <v-chip
          class="ma-2"
          >
          Cases
          </v-chip>
    </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>

       <v-list-item>
        <v-list-item-icon>
          <v-icon color="primary">
            mdi-circle
          </v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title class="display-1 text--primary">{{ Number(nigeria.recovered).toLocaleString()}}</v-list-item-title>
          <v-list-item-subtitle>  
          <v-chip
          class="ma-2"
          >
          Recovered
          </v-chip>
    </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>


       <v-list-item>
        <v-list-item-icon>
          <v-icon color="error">
            mdi-circle
          </v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title class="display-1 text--primary">{{ Number(nigeria.deceased).toLocaleString()}}</v-list-item-title>
          <v-list-item-subtitle>  
          <v-chip
          class="ma-2"
          >
          Deaths
          </v-chip>
    </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-divider></v-divider>
     
    </v-card-text>

      <p style="padding-left:20px;">Updated : Every 24 hours</p>

  
    <v-card-actions>
      <v-btn
        text
        color="deep-purple accent-4"
        to="/nigeria"
      >
        More details >>
      </v-btn>
    </v-card-actions>
  </v-card>
<br>
<br>
<div style="max-width:600px;" class="mx-auto">
 <h2 class="font-weight-bold"> Explore more countries</h2>
</div>
<br>



<v-card
    class="mx-auto"
    max-width="600"
  >
   <v-list-item three-line
   v-for="(world, i) in world"
  :key="i"
   >
      <v-list-item-content>
        
        <v-list-item-title class="font-weight-bold" color="primary">
        
          &nbsp;&nbsp;&nbsp;{{world.country}}</v-list-item-title>
          <div style="margin-left:15px;">
        <v-list-item-subtitle style="padding:0px;">
     <span style="color:green; font-size:40px;">-</span>  <b>{{ Number(world.infected).toLocaleString()}}</b> - cases
        </v-list-item-subtitle>
        <v-list-item-subtitle style="padding:0px;">
    <span style="color:blue; font-size:40px;">-</span>  <b>{{ Number(world.recovered).toLocaleString()}}</b> - Recovered
        </v-list-item-subtitle>
        <v-list-item-subtitle style="padding:0px;">
    <span style="color:red; font-size:40px;">-</span>  <b>{{ Number(world.deceased).toLocaleString()}}</b> - Deaths
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


  metaInfo() {
        return { 
            title: "Home - GoDemic",
            meta: [
                { name: 'description', content:  'Get up to date information of the coronavirus pandemic on GoDemic'},
                { property: 'og:title', content: "Home - GoDemic"},
                { property: 'og:site_name', content: 'GoDemic'},
                {property: 'og:type', content: 'website'},    
                {name: 'robots', content: 'index,follow'} 
            ]
        }
    },
    components: {
    Header,
    Footer,
  },

  data () {
    return {
      nigeria:{},
      world:{},
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
      this.nigeria = results;
    },

    
getWorld () {
        fetch("https://api.apify.com/v2/key-value-stores/tVaYRsPHLjNdNBu7S/records/LATEST?disableRedirect=true")
          .then(res => {
            return res.json();
          }).then(this.setWorld);
    },
    setWorld (results) {
      this.world = results;
    },


toLocaleString () {
      
    },



  },


  mounted(){
    this.getNigeria()
    this.getWorld()
  }


}
</script>
