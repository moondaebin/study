<template>
    <div v-for="Customer in CustomerData" :key="Customer" >
        <p v-if="Customer.cus_id==1">
            <input type="radio" name="customerName" @change="$emit('radioChange', $event.target.value)" :value="Customer.cus_id" checked> {{ Customer.cus_name }}
        </p>
        <p v-else>
            <input type="radio" name="customerName" @change="$emit('radioChange', $event.target.value)" :value="Customer.cus_id"> {{ Customer.cus_name }}
        </p>
    </div>
</template>
  <script>
  export default {
      name : 'CustomerVue',
      
      props : {
          CustomerData: Array,
      },
  }
  </script>

  <style>  
  </style>
