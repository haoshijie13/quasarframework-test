<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>Quasar CLI with Vite App</q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>Essential Links</q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>
  <q-page-container>
  <q-space/>
  <div class="row">

<div class="col q-mt-md q-ml-sm" style="max-width: 500px; width: 600px">
    <q-scroll-area 
    :thumb-style="thumbStyle"
    :content-style="contentStyle"
    :content-active-style="contentActiveStyle"
    style="height: 130px; max-width: 800px; " visible="visible" @scroll="scrollHandler">
      <q-list  padding class="row no-wrap" >
        <q-item-section top thumbnail class="q-ml-sm">
          <q-btn color="white" >
            <div>
            <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
            </div>
          </q-btn>
        </q-item-section>

        <q-item-section top thumbnail class="q-ml-none">
          <q-btn color="white" >
            <div>
            <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
            </div>
          </q-btn>
        </q-item-section>

        <q-item-section top thumbnail class="q-ml-none">
          <q-btn color="white" >
            <div>
            <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
            </div>
          </q-btn>
        </q-item-section>

      </q-list>
      <q-scroll-observer axis="horizontal" @scroll="scrollHandler" />
    </q-scroll-area >
  </div>

  <div class="col q-mt-md q-ml-sm" style="max-width: 500px; width: 600px">
    <q-scroll-area 
    :thumb-style="thumbStyle"
    :content-style="contentStyle"
    :content-active-style="contentActiveStyle"
    style="height: 130px; max-width: 800px; " visible="visible" @scroll="scrollHandler">
    <q-list  padding class="row no-wrap" >
      <q-item-section top thumbnail class="q-ml-sm">
        <q-btn color="white" >
          <div>
          <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
          </div>
        </q-btn>
        </q-item-section>

        <q-item-section top thumbnail class="q-ml-none">
        <q-btn color="white" >
          <div>
          <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
          </div>
        </q-btn>
        </q-item-section>

        <q-item-section top thumbnail class="q-ml-none">
        <q-btn color="white" >
          <div>
          <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
          </div>
        </q-btn>
        </q-item-section>

    </q-list>
    <q-scroll-observer axis="horizontal" @scroll="scrollHandler" />
    </q-scroll-area >
  </div>

  <div class="col q-mt-md q-ml-sm" style="max-width: 500px; width: 600px">
    <q-scroll-area 
    :thumb-style="thumbStyle"
    :content-style="contentStyle"
    :content-active-style="contentActiveStyle"
    style="height: 130px; max-width: 800px; " visible="visible" @scroll="scrollHandler">
    <q-list  padding class="row no-wrap" >
      <q-item-section top thumbnail class="q-ml-sm">
        <q-btn color="white" >
          <div>
          <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
          </div>
        </q-btn>
        </q-item-section>

        <q-item-section top thumbnail class="q-ml-none">
        <q-btn color="white" >
          <div>
          <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
          </div>
        </q-btn>
        </q-item-section>

        <q-item-section top thumbnail class="q-ml-none">
        <q-btn color="white" >
          <div>
          <img src="~assets/quasar-logo-inner.svg" style="width:90px;height:90px;"/>
          </div>
        </q-btn>
        </q-item-section>

    </q-list>
    <q-scroll-observer axis="horizontal" @scroll="scrollHandler" />
    </q-scroll-area >
  </div>
  
  </div>

  </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue';
import EssentialLink from 'components/EssentialLink.vue';

const linksList = [
  {
    title: 'DOCS',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev',
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework',
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev',
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev',
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev',
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev',
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev',
  },
];
const maxSize = 10000
const heavyList = []

for (let i = 0; i < maxSize; i++) {
  heavyList.push({
    label: 'Option ' + (i + 1),
    class: i % 2 === 0 ? 'q-pa-md self-center bg-grey-2 text-black' : 'q-pa-lg bg-black text-white'
  })
}
export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      contentStyle: {
        backgroundColor: 'blue',
        color: 'red-1'
      },

      contentActiveStyle: { 
        backgroundColor: '#eee',
        color: 'red-1'
      },

      thumbStyle: {
        right: '2px',
        borderRadius: '5px',
        backgroundColor: '#095231',
        width: '5px',
        opacity: '0.75'
      },

      essentialLinks: linksList,
      heavyList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
