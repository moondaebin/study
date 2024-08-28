<template>
    <div>
    <div v-for="manager in ManagerData" :key="manager">
        <ul v-if="m_id==manager.m_id &&  modal == true">
            <li>
            <label for="manager">관리담당자</label>
            <input type="text" id="manager" v-model="manager.m_name" Disabled="true">
            <button class="button_img"></button>
            </li>
            <li>
            <label for="department">**부서</label>
            <input type="text" id="department" v-model="manager.dept" Disabled="true">
            </li>
            <li>
            <label for="position">**직위</label>
            <input type="text" id="position" v-model="manager.position" Disabled="true">
            </li>
            <li>
            <label for="number2">**연락처</label>
            <input type="text" id="number2" v-model="manager.phone" Disabled="true">
            </li>
        </ul>
    </div>
  </div>
  <div>
        <ul v-if="m_id==0 && modal == true">
            <li>
            <label for="manager">관리담당자</label>
            <input type="text" id="manager" Disabled="true">
            <button class="button_img"></button>
            </li>
            <li>
            <label for="department">**부서</label>
            <input type="text" id="department" Disabled="true">
            </li>
            <li>
            <label for="position">**직위</label>
            <input type="text" id="position" Disabled="true">
            </li>
            <li>
            <label for="number2">**연락처</label>
            <input type="text" id="number2" Disabled="true">
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  import ManagerData from '../assets/manager.js';
  
  export default {
    name : 'ManagerVue',
  
    data() {
      return {
        ManagerData: ManagerData,
      }
    },
    
    props : {
        m_id : Number,
        modal:Boolean,
    },
  }
  </script>
  
  <style>
  
  </style>
