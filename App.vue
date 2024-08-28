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
          <Counsel @OpenNewCus="modal=false" @All="modal=true" :cus_id="cus_id" :modal="modal"/>
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
    .All {
      background-color:rgb(245, 244, 244);
      border: solid 2px black;
      height: 1000px;
    }
  
    .cims {
      color: white;
      background-color:deepskyblue;
      height: 50px;
      border-top: solid 2px black;
      border-left: solid 2px black;
      border-right: solid 2px black;
      padding-left: 10px;
      padding-bottom: 20px;
    }
  
    .containal {
      float: left;
    }
  
    fieldset {
      max-width: 150px;
      height: 500px;
      background-color: white;
      font-size: 20px;
      font-weight: 500;
    }
  
    #usertop {
      padding-left: 0px;
      font-weight: bold;
    }

    #usertop span, fieldset {
      margin-left: 20px;
    }
  
    #buttons input {
      width: 175px;
      height: 30px;
      background-color: deepskyblue;
      color: white;
      font-size: 20px;
      font-weight: bold;
      border-radius: 5px;
    }
  
    input[type="text"] {
      width: 170px;
      height: 30px;
    }
  
    span {
      font-size: 20px;
    }
  
    * {
      list-style: none;
    }
    /* ------------ 정보입력 ------------ */
    .infomation {
      float: left;
      margin-top: 40px;
    }

    ul {
      list-style: none;
      padding-left: 0;
    }

    ul li {
      margin: 20px;
    }

    li label {
      width: 120px;
      line-height: 36px;
      float: left;
      font-weight: bold;
      text-align: right;
      margin-right: 10px;
    }
    
    .manager ul li:first-child { 
      position: relative;
      display: flex;
    }

    .manager ul li:first-child input { 
      width: 55%;
    }

    .manager ul li:first-child button {
      background: url(./assets/search.png) no-repeat;
      background-size: cover;
      width: 30px;
      height: 30px;
      border-width: 0;
      position: absolute;
      right: 5px;
      top: 3px;
    }
  
    /* ------------ 상담내역 ------------ */

    .details {
      float: left;
      margin-left: 20px;
    }
  
    .details h3 {
        margin-left: 10px;
    }

    .detail_box {
      width: 500px;
      height: 565px;
      margin: 10px;
      padding: 5px;
      border: 1px solid gray;
      border-radius: 1px;
    }

    .btn {
      max-width: 150px;
      height: 40px;
      width: 123px;
      align-items: center;
      font-size: 20px;
      font-weight: 700;
      color: white;
      background-color: deepskyblue;
      text-decoration: none;
      cursor: pointer;
      margin-left: 7px;
      margin-right: auto;
      margin-bottom: 10px;
      border-radius: 5px;
      transition: 0.5s;
    }
  
    .inquiry {
      background-color: rgb(228, 195, 152);
      color: black;
    }
  </style>
