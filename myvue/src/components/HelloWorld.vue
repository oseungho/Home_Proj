<script setup>
  import { ref } from 'vue'
  import menuList from '@/pagejs/asideMenu'

  const openedMenus = ref([])

  const toggleSubMenu = (index) => {
    const isOpened = openedMenus.value.includes(index)
    if (isOpened) {
      openedMenus.value = openedMenus.value.filter(item => item !== index)
    } else {
      openedMenus.value.push(index)
    }
  }
</script>

<template>
  <v-row no-gutters>
    <v-col cols="2">
      <v-container class="main-Area">
        <aside>
          <div>
            sidebar            
          </div>

          <ul v-if="menuList.length > 0">           
            <li v-for="(menu, index) in menuList" :key="index" class="nav-link" @click="toggleSubMenu(index)">
              <div style="border: solid 1px black;">
                <a href="#">{{ menu.title }}</a>
              </div>
              <!-- 자식 메뉴가 있는 경우에만 렌더링 -->
              <ul v-if="menu.children && openedMenus.includes(index)">
                <li v-for="(child, childIndex) in menu.children" :key="childIndex" class="nav-link">
                   <a href="#">{{ child.title }}</a>
                </li>
              </ul>
            </li>
          </ul>    
        </aside>
      </v-container>
    </v-col>
    <v-col cols="10">
      <v-container class="main-Area">
        main
      </v-container>
    </v-col>
  </v-row>
</template>

<style>
.main-Area{
  border: solid 2px red;
}

.nav-link a {
    display: flex;
    align-items: center;
  }
</style>
