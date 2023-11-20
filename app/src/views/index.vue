<template>
    <q-layout view="lHh Lpr lFf">
      <q-header elevated class="glossy">
        <q-toolbar>
          <q-btn
            flat
            dense
            round
            @click="leftDrawerOpen = !leftDrawerOpen"
            aria-label="Menu"
            icon="menu"
          />
  
          <q-toolbar-title>Flower App</q-toolbar-title>
  
          <!-- <div>Quasar v{{ $q.version }}</div> -->
        </q-toolbar>
      </q-header>
  
      <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="bg-grey-2">
        
        <q-list>
          <q-item-label header>This is a Drop menu</q-item-label>
          
          <q-item clickable tag="a" target="_blank" href="https://quasar.dev">
            <q-item-section avatar>
              <q-icon name="school" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Menu One</q-item-label>
              <q-item-label caption>Item One</q-item-label>
            </q-item-section>
          </q-item>

          <q-item
            clickable
            tag="a"
            target="_blank"
            href="#"
          >
            <q-item-section avatar>
              <q-icon name="code" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Menu Two</q-item-label>
              <q-item-label caption>Item Two</q-item-label>
            </q-item-section>
          </q-item>

          <q-item
            clickable
            tag="a"
            target="_blank"
            href="https://chat.quasar.dev"
          >
            <q-item-section avatar>
              <q-icon name="chat" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Menu Three</q-item-label>
              <q-item-label caption>Item Three</q-item-label>
            </q-item-section>
          </q-item>

          <q-item
            clickable
            tag="a"
            target="_blank"
            href="https://forum.quasar.dev"
          >
            <q-item-section avatar>
              <q-icon name="forum" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Menu Four</q-item-label>
              <q-item-label caption>Item Four</q-item-label>
            </q-item-section>
          </q-item>

          <q-item
            clickable
            tag="a"
            target="_blank"
            href="https://twitter.com/quasarframework"
          >
            <q-item-section avatar>
              <q-icon name="rss_feed" />
            </q-item-section>
            <q-item-section>
              <q-item-label>Menu Five</q-item-label>
              <q-item-label caption>item Five</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-drawer>
  
      <q-page-container>
        <HelloWorld />
      </q-page-container>
    </q-layout>
  </template>
  
<script>
  import { onMounted, ref } from "vue";
  import HelloWorld from '../components/kakaoMap.vue'

  // onMounted(() =>{
  //   console.log("Config Mode : " , process.env.VUE_APP_MODE)
  // })

  export default {

    name: "index",
  
    components: {
      HelloWorld,
    },
  
    setup() {
      const leftDrawerOpen = ref(false)

      onMounted(()=>{
        console.log("Config Mode : " , process.env.VUE_APP_MODE)
        // leftDrawerOpen.value = !leftDrawerOpen.value
      })

      return {
        leftDrawerOpen
      };
      
    },
    
  };
</script>
  