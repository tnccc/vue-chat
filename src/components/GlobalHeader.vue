<script setup lang="ts">
import { ref } from 'vue';

interface Props {
  loginStatus?: boolean,
}

const props = withDefaults(defineProps<Props>(), {
  
})

const isHideNavigation = ref(false)

const afterLoginMenus = ref([
  {
    id: '1',
    name: '参加者一覧',
  },
  {
    id: '2',
    name: 'ログアウト',
    path: '/'
  }
])

</script>

<template>
  <header :class="$style.header">
    <div
      :class="$style.container"
    >
      <h1>ONEDAY CHAT</h1>
      <div
        :class="$style.menu"
      >
        <button
          @click="isHideNavigation = !isHideNavigation"
        >
          <span>MENU</span>
        </button>
        <div
          v-show="loginStatus"
          :class="[
            $style.dropdown, 
            isHideNavigation ? $style.open : ''
          ]"
        >
          <div
            :class="$style.dropdown_container"
          >
            <ul
              :class="$style.list"
            >
              <li
                v-for="item in afterLoginMenus"
                :key="item.id"
                :class="$style.item"
              >
                {{ item.name }}
              </li>
            </ul>
          </div>
        </div>
        
      </div>
    </div>
  </header>
</template>

<style lang="scss" module>
.header {
  padding         : calc(var(--bv) * 3);
  display         : flex;
  color           : var(--white);

  .container {
    display        : flex;
    width          : 100%;
    align-items    : center;
    justify-content: space-between;

    h1 {
      font-size: var(--font-size-medium);
    }
  }

  .menu {
    display       : inline-block;
    z-index: var(--z-index-max);
    
    span {
      font-size     : var(--font-size-small);
      font-weight   : bold;
      letter-spacing: .1em;
      color         : var(--white);
      cursor        : pointer;
    }
  }

  .dropdown {
    font-size  : var(--font-size-small);
    font-weight: bold;

    &_container {
      position : relative;

      .list {
        position        : absolute;
        top             : -30px;
        padding         : calc(var(--bv) * 2);
        min-width       : 360px;
        right           : 0;
        opacity         : 0;
        visibility      : visible;
        color           : var(--white);
        background-color: var(--dark-black);
        transition      : opacity .3s, top .3s, visibility .3s;
        z-index         : -1;

        li + li {
          margin-top: var(--bv);
        }
      }
    }

    &.open {
      .list {
        top       : 100%;
        opacity   : 1;
        visibility: visible;
      }
    }
  }  
}

</style>