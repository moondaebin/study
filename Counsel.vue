<template>
    <div>
    <div class="detail_box">
        <div v-for="counsel in CounselData" :key="counsel">
            <p v-if="cus_id==counsel.cus_id && modal==true">
              {{ counsel.date + ' ' + counsel.time + ' ' + counsel.content }}
            </p>
        </div>   
    </div>
    <div>
            <button class="btn register">등록</button>
            <button class="btn update">변경</button>
            <button class="btn delete">삭제</button>
            <button class="btn new" @click="$emit('OpenNewCus')">신규</button>
          </div>
    
      <div>
        <button class="btn inquiry" @click="All">고객조회</button>
      </div>
    </div>
  </template>
  
  <script>
  // import counsel from '../assets/counsel.js';
  import CounselData from '../assets/counsel.js';
  
  export default {
    name : 'ConselVue',
  
    data() {
      return {
        CounselData: CounselData,
        condition : true,
      }
    },
  
    props : {
        cus_id : Number,
        modal : Boolean,
        Counsel : String,
  
    },
  
    methods: {
      All() {
        if(this.check()) {
          this.send();
        }
      },
      send() {
        this.$emit('All')
      },
      check() {
          let dop = document.querySelector("#dop")
          let name = document.querySelector("#name")
          let resident = document.querySelector("#resident")
          let email = document.querySelector("#email")
          let phone = document.querySelector("#phone")
          let job = document.querySelector("#job")
          if (dop.value == '') {
            alert("작성일자를 입력하세요")
            dop.focus();
          } else if (name.value == '') {
            alert("성함을 입력하세요")
          } else if (resident.value == '') {
            alert("주민번호를 입력하세요")
          } else if (email.value == '') {
            alert("이메일을 입력하세요")
          } else if (phone.value == '') {
            alert("전화번호를 입력하세요")
          } else if (job.value == '') {
            alert("직업을 입력하세요")
          } else {
            return this.condition;
          }
  
      },
      
    },
    // mounted() {
    //       let button =document.querySelector(".button_img")
    //       let ID = document.querySelector("#name")
    //       button.addEventListener('click' , () => {
    //           alert(ID.value)
    //       })
  
    //   },
  }
  </script>
  
  <style>
  
  </style>
