<template>
  <div>
    <div class="cims">
      <h2>고객정보 관리</h2>
    </div>
  
    <div class="All">
    <div class="containal">
        <ul id="usertop">
          <span>고객성명:</span>
          <li>
            <input type="text" @input="this.keyword=$event.target.value" :value="keyword">
          </li>
      
          <div id="buttons">
            <li>
              <input type="button" @click="searchPart(keyword)" value="조건 검색">
            </li>
            <li>
              <input type="button" @click="searchAll()" value="전체 검색">
            </li>
          </div>
        </ul>
      
          <fieldset>
            <Customer :CustomerData="CustomerData" @radioChange="cus_id=$event" />
          </fieldset>
        </div>
      
        <!-------------------- 정보 입력 부분 ----------------------->
      
        <div class="infomation">
          <CustDetail :CustomerData="CustomerData" :cus_id="cus_id" :modal="modal"/>
          <hr>
            <div class="manager" v-for="Customer in CustomerData" :key="Customer" >
              <Manager v-if="cus_id == Customer.cus_id" :m_id="Customer.m_id" :modal="modal"/>
          </div> 
        </div>

        <NewCus :modal="modal"/>

        <!-------------------- 상담 내역 부분 ----------------------->
      
        <div class="details">
          <h3>상담내역:</h3>
          <Counsel @OpenNewCus="modal=false"
                 @CloseNewCus="modal=true"
                 @All="modal=true"
                :cus_id="cus_id" :modal="modal"/>
          <!-- <div class="detail_box">상담내용 들어갈 자리</div> -->
    
          <!-- <div>
            <button class="btn register">등록</button>
            <button class="btn update">변경</button>
            <button class="btn delete">삭제</button>
            <button class="btn new">신규</button>
          </div>
    
          <div>
            <button class="btn inquiry">고객조회</button>
          </div> -->
        </div>
      </div>
    </div>
  </template>

  <script>  
  import Customer from './components/Customer.vue';
  import CustomerData from './assets/customer.js';
  import CustDetail from './components/CustDetail.vue';
  import Manager from './components/Manager.vue';
  import Counsel from './components/Counsel.vue';
  import NewCus from './components/NewCus.vue';

  export default {
    name : 'App',
    data() {
      return {
        searchData : [],
        originData : [...CustomerData],
        CustomerData : CustomerData,
        cus_id : 1,
        keyword : '',
        modal : true,
      }
    },

    methods : {
     // includes 함수, 문자열 검색
      searchPart () {
        this.searchData = [];

        for(let i=0; i<this.CustomerData.length; i++){
          if(this.keyword == ''){
            return alert('검색어를 입력해 주세요.');
          }else if(this.CustomerData[i].cus_name.includes(this.keyword)){
            this.searchData.push(this.CustomerData[i]);
          }
        }
        this.CustomerData = this.searchData;
        this.cus_id = 0;
      },

      searchAll(){
        this.CustomerData = [...this.originData];
        this.cus_id = 1;
      },
    },
    
    components: {
      Customer,
      CustDetail,
      Manager,
      Counsel,
      NewCus,
    },
  }
  </script>
  <style>
     @import './assets/css/app.css';
  </style>
