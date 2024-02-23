<template>
    
   
  <q-layout view="hHh Lpr lff" class="fullscreen">
    <q-drawer
        v-model="drawer"
        show-if-above

        :mini="!drawer || miniState"
        @click.capture="drawerClick"

        :width="300"
        :breakpoint="500"
        bordered
        
        :class="$q.dark.isActive ? 'bg-indigo-13' : 'bg-indigo-14'"
      >
        <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: 0 }">
          <q-list padding>
            <br>
            <q-item class="q-ma-2xl text-white" clickable v-ripple>
              <!-- <q-item-section avatar>
                <q-icon name="T"></q-icon>
              </q-item-section> -->

              <q-item-section class="text-h5 text-center text-weight-bold">
                TELECALLING
              </q-item-section>
            </q-item>
            <br>
            <br>
            <q-item clickable v-ripple>
              <q-item-section class="text-white" avatar>
                <q-icon name="call"></q-icon>
              </q-item-section>

              <q-item-section class="text-grey-4 text-h6">
                Call Logs
              </q-item-section>
            </q-item>
            <br>
            <q-item clickable v-ripple>
              <q-item-section class="text-white" avatar>
                <q-icon name="account_box"></q-icon>
              </q-item-section>

              <q-item-section class="text-grey-4 text-h6">
                Calls
              </q-item-section>
            </q-item>
            <br>
            <q-item class="text-white" clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="equalizer"></q-icon>
              </q-item-section>

              <q-item-section class="text-grey-4 text-h6">
                Leads
              </q-item-section>
            </q-item>
            <br>
            <q-item class="text-white" clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="fact_check"></q-icon>
              </q-item-section>

              <q-item-section class="text-grey-4 text-h6">
                Follow Up
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <!--
          in this case, we use a button (can be anything)
          so that user can switch back
          to mini-mode
        -->
        <div class=" absolute" style="top: 35px; right: -17px">
          <q-btn
          text-color="indigo-14"
            dense
            round
            unelevated
            color="white"
            icon="chevron_left"
            @click="miniState = true"
          ></q-btn>
          <!-- <div class="q-mini drawer-close absolute" style="top: 15px; right: -17px">
          <q-btn
            dense
            round
            unelevated
            color="blue"
            icon="chevron_right"
            @click="miniState = true"
          ></q-btn> -->
        </div>
      </q-drawer>

<q-page-container>
<router-view />
</q-page-container>

<q-footer  class="bg-white  mobile-only">
<q-toolbar class="q-mb-lg">
  <q-toolbar-title>
   
      <q-tabs
      v-model="tab"
      inline-label
      switch-indicator
      indicator-color="primary"
      class="bg-indigo-14 text-white shadow-2 rounded-borders"
      
    >
      <q-tab  icon="more_horiz"  class="butn"/>
      <q-tab   icon="call" class="butn1"/>
      <q-tab   icon="account_box" class="butn2" />
      <q-tab   icon="equalizer"  class="butn3"/>
      <q-tab  icon="fact_check"  class="butn4"/>
    </q-tabs>
  </q-toolbar-title> 
</q-toolbar>

</q-footer>

</q-layout>
 
  </template>
  
  <script>
  
  import { ref } from 'vue'

export default {
setup () {
  const miniState = ref(false)

  return {
    drawer: ref(false),
    miniState,

    drawerClick (e) {
      // if in "mini" state and user
      // click on drawer, we switch it to "normal" mode
      if (miniState.value) {
        miniState.value = false

        // notice we have registered an event with capture flag;
        // we need to stop further propagation as this click is
        // intended for switching drawer to "normal" mode only
        e.stopPropagation()
      }
    },
    mounted(){
      feather.replace();

document.querySelector("q-tab").focus();
    }
    

  }
}
}
  </script>
  <style scoped>
</style>