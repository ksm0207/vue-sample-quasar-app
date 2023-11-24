<template>
    <div>
      <q-layout view="hHh lpr fff" >
        <q-header elevated >
        <q-toolbar>
          <q-btn
            flat
            dense
            round
            @click="leftDrawerOpen = !leftDrawerOpen"
            aria-label="Menu"
            icon="menu"
          />
  
          <q-toolbar-title>App Title</q-toolbar-title>
  
          <!-- 검색바 -->
          <q-input dark dense standout v-model="text" input-class="text-right" class="q-ml-md" placeholder="검색하세요."  >
          <template v-slot:append>
            <q-icon v-if="text === ''" name="search" />
            <q-icon v-else name="clear" class="cursor-pointer" @click="text = ''" />
          </template>
        </q-input>

        <!-- 상호작용 버튼  -->
        <q-btn flat icon="question_answer" />
        <q-btn flat icon="favorite_border" />
        <q-btn flat icon="perm_identity" />

        </q-toolbar>
      </q-header>

        <q-drawer v-model="leftDrawerOpen"
        side="left"
        show-if-above
        :width="200"
        :breakpoint="100"
        elevated

         class="bg-grey-2">
          <q-list>
            <q-item-label header>This is a Drop menu</q-item-label>
            
            <!-- Drop Menu Start -->
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
            <!-- Drop Menu end -->
          </q-list>
        </q-drawer>



        <q-page-container>
          <q-page padding>
            <HelloWorld />
          </q-page>
        </q-page-container>
     
    </q-layout>
    </div>
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
      const text = ref('')

      onMounted(()=>{
        console.log("Git Test")
        console.log("Config Mode : " , process.env.VUE_APP_MODE)
        // leftDrawerOpen.value = !leftDrawerOpen.value
      })

      return {
        leftDrawerOpen,
        text
      };
      
    },
    
  };
</script>
  