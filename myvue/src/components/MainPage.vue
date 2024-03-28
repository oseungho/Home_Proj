<script setup>
  import { ref, computed } from 'vue'
  import menuList from '@/pagejs/asideMenu'
  import Main from '@/components/Main.vue'
  import Vue from '@/components/Vue.vue'
  import Selenium from '@/components/Selenium.vue'
  import BeautifulSoup from '@/components/BeautifulSoup.vue'
  import Java from '@/components/Java.vue'
  import Top from '@/Top.vue'

  const openedMenus = ref([])

  const toggleSubMenu = (index) => {
    const isOpened = openedMenus.value.includes(index)
    if (isOpened) {
      openedMenus.value = openedMenus.value.filter(item => item !== index)
    } else {
      openedMenus.value.push(index)
    }
  }

  const selectedMenu = ref('Main') // 초기값으로 'Main' 문자열 설정

  const showContent = (title) => {
    console.log(title , ' 클릭')
    selectedMenu.value = title.toLowerCase() // 클릭한 메뉴의 title을 소문자로 변경하여 할당
    console.log('현재 selectedMenu의 값 : ', selectedMenu.value)
  }

  // 선택된 메뉴의 컴포넌트를 반환하는 계산된 속성
  const selectedComponent = computed(() => {
    switch (selectedMenu.value) {
      case 'main':
        return Main
      case 'vue':
        return Vue
      case 'selenium':
        return Selenium
      case 'beautifulsoup':
        return BeautifulSoup
      case 'java':
        return Java
      default:
        return Main
    }
  })
</script>

<template>
  <div class="main-page">
    <Top class="top-container"/>
    <v-row no-gutters>
      <v-col cols="2" class="main-Area" style="border-right:3px solid gray">
        <v-container>
          <aside>
            <div @click="showContent('Main')">
              <h3>sidebar</h3>
            </div>

            <ul v-if="menuList.length > 0">           
              <li v-for="(menu, index) in menuList" :key="index" class="nav-link">
                <div @click="toggleSubMenu(index)">
                  <!-- 자식 속성이 있는 경우는 Main Content 변경 안되도록 -->
                  <a v-if="menu.children" href="#">{{ menu.title }}</a>
                  <!-- 자식 속성이 없는 경우 -->
                  <a v-else href="#"  @click="showContent(menu.title)">{{ menu.title }}</a>                  
                </div>
                <!-- 자식 메뉴가 있는 경우에만 렌더링 -->                
                <ul style="margin-left: 15px;" v-if="menu.children && openedMenus.includes(index)">
                  <li v-for="(child, childIndex) in menu.children" :key="childIndex" class="nav-link">
                    <a href="#" @click="showContent(child.title)">{{ child.title }}</a>
                  </li>
                </ul>
              </li>
            </ul>    
          </aside>
        </v-container>
      </v-col>
      <v-col cols="10" class="main-Area">      
        <v-container>
          <component :is="selectedComponent" /> <!-- 선택된 메뉴에 대한 컴포넌트 표시 -->        
        </v-container>
      </v-col>
    </v-row>
  </div>
</template>

<style>
.main-page {
  width: 100%; /* 부모 컨테이너가 100% 너비를 차지하도록 설정 */
  border: solid 3px gray;
}

/* Top.vue 컴포넌트의 스타일 */
.top-container {
  border-bottom: solid 3px gray;
  width: 100%; /* 최상단 컨테이너가 가득 차도록 너비를 100%로 설정 */
  height: 50px;
  /* margin-bottom: 5px; */
}

.main-Area{
  /* border: solid 2px red; */
}

.nav-link a {
    display: flex;
    align-items: center;
}
</style>
