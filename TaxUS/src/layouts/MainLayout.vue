<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          TaxUS
        </q-toolbar-title>

        <div>App v1.0</div>
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Tax assistant</div>
        <div class="text-subtitle1">{{todaysDate}}</div>
      </div>
      <q-img src="..\statics\head-tax.jpg"
          class="header-image absolute-top" />
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="800"
      >
        <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
          <q-list padding>

            <q-item to="/" exact clickable v-ripple>  
              <q-item-section avatar>
                <q-icon name="check_circle" />
              </q-item-section>
              <q-item-section>
                Deals
              </q-item-section>
            </q-item>
            
            <q-item to="/Income" exact clickable v-ripple>  
              <q-item-section avatar>
                <q-icon name="attach_money" />
              </q-item-section>
              <q-item-section>
                Income
              </q-item-section>
            </q-item>

            <q-item to="/Costs" exact clickable v-ripple>  
              <q-item-section avatar>
                <q-icon name="money_off" />
              </q-item-section>
              <q-item-section>
                Costs
              </q-item-section>
            </q-item>

            <q-item to="/help" exact clickable v-ripple>  
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>
              <q-item-section>
                Help
              </q-item-section>
            </q-item>

          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="../statics/background.jpg" style="height: 192px; color: $primary;">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="../statics/avatar.jpg">
            </q-avatar>
            <div class="text-weight-bold">Arctic Fox</div>
            <div>@arcticfox_usa</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import EssentialLink from '../components/EssentialLink.vue'
import { date } from 'quasar'

const linksData = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  }
]

import { Vue, Component } from 'vue-property-decorator'

@Component({
  components: { EssentialLink }
})
export default class MainLayout extends Vue {
  leftDrawerOpen = false;
  essentialLinks = linksData;

  timeStamp = Date.now();
  todaysDate = date.formatDate(this.timeStamp, 'dddd D MMMM');
}
</script>

<style lang="scss">
  .header-image {
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter: grayscale(100%);
  }
</style>
