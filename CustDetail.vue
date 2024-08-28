<template>
  <div>
  <div class="cust" v-for="customer in CustomerData" :key="customer">
        <ul
        v-if="cus_id == customer.cus_id &&  modal == true">
          <li>
            <label for="dop">**작성일자</label>
            <input type="text" id="dop" v-model="customer.create_date"  Disabled="true">
          </li>
          <li>
            <label for="name">*고객명</label>
            <input type="text" id="name" v-model="customer.cus_name" Disabled="true">
          </li>
          <li>
            <label for="resident">*실명번호</label>
            <input type="text" id="resident" v-model="customer.jumin_id" Disabled="true">
          </li>
          <li>
            <label for="email">*E-mail</label>
            <input type="text" id="email" v-model="customer.email" Disabled="true">
          </li>
          <li>
            <label for="number">전화번호</label>
            <input type="text" id="number" v-model="customer.tel" Disabled="true">
          </li>
          <li>
            <label for="phone">*핸드폰번호</label>
            <input type="text" id="phone" v-model="customer.phone" Disabled="true">
          </li>
          <li>
            <label for="job">*직업</label>
            <input type="text" id="job" v-model="customer.job" Disabled="true">
          </li>
          <li>
            <label for="address">주소</label>
            <textarea cols="20" rows="3" v-model="customer.addr" Disabled="true"></textarea>
          </li>
          </ul>
        </div> 
        <customer/>
      </div>
      
</template>

<script>


export default {
    name : 'CustDetailVue',



    components : {

    },

    props : {
        CustomerData: Array,
        cus_id : Number,
        modal : Boolean,
    }
}
</script>

<style>

</style>
