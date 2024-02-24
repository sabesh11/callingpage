<template>
  <div class="row justify-between q-mt-md mobile-only items-center">
      <div class="col-5 self-center ">
          <p class="text-h5 text-center text-black text-weight-bold">Telecalling</p>
      </div>
      <div class="col-5 self-center">
          <div class="row">
              <div class="col-6 ">
                  <span class="text-h6 text-black text-weight-bold">Deadpool</span>
                  <div class="row justify-end">
                      <q-item-label caption class="text-end text-grey-8 text-weight-bold">user</q-item-label>
                  </div>
  
              </div>
              <div class="col-2 self-start">
                  <q-item clickable class="itt">
  
                      <q-item-section avatar>
                          <q-avatar color="grey" text-color="white">
  
                          </q-avatar>
                      </q-item-section>
                  </q-item>
              </div>
          </div>
      </div>
  </div>
  <div class="q-pa-sm example-row-equal-width cll q-mt-md">
  
      <div class="row q-ml-md q-mt-lg">
  
          <p class="text-body1 text-grey-8 text-weight-bold mobile-only">Calls</p>
          <p class="text-h5 text-grey-8 text-weight-bold desktop-only q-ml-md">Calls</p>
          
      </div>
      <div class="row justify-around ">
        <div class="col-12 col-md-5 q-mt-lg" @click="fullHeight = true" v-for="callers in callDetails" :key="callers">
            <div class="row justify-between">
                <div class="col-2 ">
                    <q-item clickable>

                        <q-item-section avatar>
                            <q-avatar color="indigo-14" text-color="white">

                            </q-avatar>
                        </q-item-section>
                    </q-item>
                    <!-- <q-img rounded src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSZ63k8LAmwJJxlKvu88GBE_Svx-ad-rsWiZ0C4sZUwWA&s" class="rounded"></q-img> -->
                </div>
                <div class="col-4 col-md-5">
                    <span class="text-black text-weight-medium text-body2">+91 {{ callers.phoneno }}</span><br>
                    <span class="text-grey text-weight-medium  text-body2">{{ callers.callername }}</span>
                </div>
                <div class="col-5 col-md-5">
                    <span class="text-grey text-weight-medium text-body2">{{ callers.email }}</span><br>
                    <span class="text-black  text-body2 text-weight-medium">{{ callers.course }}</span>
                </div>
            </div>
        </div>
        
      </div>
      <q-dialog v-model="fullHeight" full-width>
          <q-card>
              <q-card-section class="row  ">
                  <div class="text-h5 text-black text-weight-bold">Call details</div>
                  <q-space />
                  <q-btn icon="close" flat round dense v-close-popup />
              </q-card-section>
  
              <q-card-section>
                  <div class="row">
                      <div class="col-md-6 col-12 q-mt-md">
                          <div class="column" style="max-width: 400px;">
                              <q-label>Name</q-label>
                              <input outlined v-model="text" />
                          </div>
                          <div class=" column q-mt-md" style="max-width: 400px">
                              <q-label>Age</q-label>
                              <input outlined v-model="text" />
                          </div>
                          <div class=" column q-mt-md" style="max-width: 400px">
                              <q-label>Alternative Contact</q-label>
                              <input outlined v-model="text" />
                          </div>
  
                          <div class=" column q-mt-md" style="max-width: 400px">
                              <q-label>mode</q-label>
                              <div class="q-gutter-sm">
                                  <q-radio v-model="shape" val="online" label="online" />
                                  <q-radio v-model="shape" val="offline" label="offline" />
  
                              </div>
                              <div class=" column q-mt-md" style="max-width: 400px">
                                  <q-label>Qualification</q-label>
                                  <select outlined v-model="text" style="height: 30px;"></select>
                              </div>
                              <div class=" column q-mt-md" style="max-width: 400px">
                                  <q-label @click="date= true">Follow up date</q-label>
  <!-- <input type="date" outlined v-model="text" style="height: 30px;"/> -->
                                  
  <VueDatePicker v-model="date" outlined></VueDatePicker>   
  
  
                              </div>
                          </div>
                      </div>
                      <div class="col-md-6 col-12 q-mt-md">
                          <div class=" column" style="max-width: 400px">
                              <q-label>Email</q-label>
                              <input outlined v-model="text" />
                          </div>
                          <div class=" column q-mt-md" style="max-width: 400px">
                              <q-label>Contact</q-label>
                              <input outlined v-model="text" />
                          </div>
                          <div class=" column q-mt-md" style="max-width: 400px">
                              <q-label>Course</q-label>
                              <select outlined v-model="text" style="height: 30px;"></select>
                          </div>
  
                          <div class=" column q-mt-md" style="max-width: 400px">
                              <q-label>Remark</q-label>
                              <textarea outlined v-model="text"></textarea>
                          </div>
  
                          <div class="row justify-start q-mt-md">
                              <button flat class="text-white bg-indigo-14 no-border rounded-borders" style="width:400px; height: 50px;">Save</button>
                          </div>
  
                      </div>
                  </div>
              </q-card-section>
  
          </q-card>
      </q-dialog>
  
  </div>
  </template>
  
  <script>
  import VueDatePicker from '@vuepic/vue-datepicker';
  import '@vuepic/vue-datepicker/dist/main.css'
  
  import {
      ref
  } from 'vue'
  export default {
      name: "CallingComp",
      components: { VueDatePicker },
      data() {
          return {
            date: null,
  
              fullHeight: ref(false),
              callDetails:[
                {
                    phoneno: 8248952135,
                    callername:"Batman",
                    email:"batman@gmail.com",
                    course:"Full Stack Developer",

                },
                {
                    phoneno: 8248952135,
                    callername:"Batman",
                    email:"batman@gmail.com",
                    course:"Full Stack Developer",

                }
            ]
          }
      },
      
  
  }
  </script>
  
  <style>
  .q-dialog__inner--fullwidth>div {
      width: 100% !important;
      max-width: 100% !important;
  }
  
  @media (min-width:480px) {
      .q-dialog__inner--fullwidth>div {
          width: 80% !important;
          max-width: 100% !important;
      }
  }
  
  .q-field__control {
      color: var(--q-primary);
      /* height: 56px; */
      /* height: 90%; */
      max-width: 100%;
      outline: none;
  }
  
  .q-field__native {
      /* min-height: 56px; */
      height: 90%;
      max-width: 100%;
      outline: none;
  }
  
  .itt {
      min-height: 48px;
      padding: 1px 11px;
      color: inherit;
      transition: color 0.3s, background-color 0.3s;
  
  }
  
  .q-item__label {
      line-height: 0.6em !important;
      max-width: 80%;
  }
  
  * {
      cursor: pointer;
      letter-spacing: 2;
  }
  </style>
  