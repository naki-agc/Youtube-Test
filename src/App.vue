<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipped flating temporary>
      <v-list>
        <v-row class="ma-2 mb-3">
         <v-icon class="mx-4" large>mdi-video</v-icon>
        <v-toolbar-title class="align-center">
            <span class="title">Ali naki</span>
        </v-toolbar-title>
        </v-row>
        <v-list-item v-for="item in items" :key="item.icon" link>
          <v-list-item-actions>
            <v-icon>{{item.icon}}</v-icon>
            </v-list-item-actions>
            <v-list-item-content>
            <v-list-item-title>
              {{item.text}}
            </v-list-item-title>
            </v-list-item-content>
        </v-list-item>

        <v-divider/>
      </v-list>
      
    </v-navigation-drawer>
    <v-app-bar app clipped-lefts>
      <v-app-bar-nav-icon @click="drawer=!drawer"/>
      <v-icon class="mx-4" large>mdi-video</v-icon>
        <v-toolbar-title class="align-center">

            <v-btn :href="`https://www.linkedin.com/in/ali-agca`" >
            <v-icon >mdi-linkedin</v-icon>
            Linkedin adresim için tıklayınız
            </v-btn>
           
 
        </v-toolbar-title>
        <v-spacer/>
        <v-text-field class="mt-7" solo aria-placeholder="Ara..." single-line append-icon="mdi-magnify" color="white"/>
      <v-spacer/>
      <v-btn class="ml-0" icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
       <v-btn class="ma-2" icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <div>
        <v-menu v-model="menu" :close-on-content-click="false" :nudge-width="250" offset-x>
        <template v-slot:activator="{on}">
          <v-avatar size="40">
            <img v-on="on" src="https://media-exp1.licdn.com/dms/image/C4E03AQFAOEPz6jxgOg/profile-displayphoto-shrink_800_800/0/1629324686786?e=1649894400&v=beta&t=m2p-qgYmhDRZWZrhL6qBTG8k7YEKRNTCOgY9S7-ZyUo">
          </v-avatar>
        </template>
        <v-card>
          <v-list>
            <v-list-item>
              <v-list-item-avatar></v-list-item-avatar>
            <v-list-item-content>
            <v-list-item-title>ALİ NAKİ AĞCA</v-list-item-title>
            <v-list-item-subtitle>Software developer</v-list-item-subtitle>
            </v-list-item-content>
            </v-list-item>
          </v-list>
          <v-divider/>
          <v-list>
           <v-list-item>
             <v-list-item-action>
               <v-icon>mdi-cog</v-icon>
             </v-list-item-action>
             <v-list-item-title>Ayarlar</v-list-item-title>
           </v-list-item>
          </v-list>
          <v-list>
           <v-list-item>
             <v-list-item-action>
               <v-switch v-model="theme" color="purple" @click="dark()"></v-switch>
             </v-list-item-action>
             <v-list-item-title>Karanlık Tema</v-list-item-title>
           </v-list-item>
          </v-list>
          <v-card-actions>
            <v-spacer/>
            <v-btn color="primary" text @click="menu=false">
            Çıkış yap
            </v-btn>
          </v-card-actions>
        </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    
    <v-content>
      <v-container>
        <v-row class="mb-4">
          <v-col sm="6" md="4" lg="3" xl="2" v-for="(item,index) in 200" :key="index">
          <v-card>
           <v-img height="200px" :src="`https://picsum.photos/500/300/?image=${(index+1)}`" 
           :lazy-src="`https://picsum.photos/10/6/?image=${(index+1)}`" ></v-img>
            <v-card-sub-title class="">Number {{item}}</v-card-sub-title>
            <v-card-text class="text--primary"><div>Başlık Alanı</div><div>Başlık İçeriği</div></v-card-text>
            <v-card-actions>
              <v-btn color="red" text>Kaydet</v-btn>
              <v-btn color="red" text>Paylaş</v-btn>
            </v-card-actions>
          </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  data: () => ({

    items:[
      {icon:"mdi-trending-up",text:"Popüler içerik"},
      {icon:"mdi-youtube-subscription",text:"Takip"},
      {icon:"mdi-history",text:"Geçmiş"},
      {icon:"mdi-playlist-play",text:"Popüler içerik"},
      {icon:"mdi-clock",text:"Popüler içerik"},
    ],
    menu:false,
    theme:false,
    drawer:false
  }),

  methods: {
    dark(){
      if(this.theme==true){
        this.$vuetify.theme.dark=true
      }
      else{
        this.$vuetify.theme.dark=false
      }
    }
  }

};
</script>
