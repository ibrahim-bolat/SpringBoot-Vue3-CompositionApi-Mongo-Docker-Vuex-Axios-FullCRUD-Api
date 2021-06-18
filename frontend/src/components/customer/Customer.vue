<template>
  <tr>
    <td>{{ index+1}}</td>
    <td>{{ customer.customerName }}</td>
    <td>{{ customer.customerSurName }}</td>
    <td>{{ customer.language }}</td>
    <td>{{ customer.gender }}</td>
    <td>{{ customer.phoneNumber }}</td>
    <td>{{ customer.email }}</td>
    <td>{{ format_date(customer.birthofDate) }}</td>
    <td>
      <button type="button" class="btn btn-primary" @click="showModal();updateCustomer(customer)">Düzenle</button>
    </td>
    <td><button type="button" class="btn btn-danger" @click="deleteCust(customer.customerId)">Sil</button></td>
  </tr>
</template>

<script>
import moment from "moment";
import {ref} from "vue"
import { useStore } from 'vuex'

export default {
  name: "Customer",
  props: ["customer","index"],
  setup(){
    const store = useStore()
     let displayModal= ref(false);
      const showModal=()=>{
        store.dispatch('changeDisplayModal', true)
       };
      const deleteCust=(id)=>{
        store.dispatch('deleteCustomer', id)
       };
       const updateCustomer=(customer)=>{
        store.dispatch('updateCustomer', customer)
       };
       const format_date=(value)=> {
      return moment(value).format("DD/MM/YYYY");
    };
    return {
      displayModal,showModal,deleteCust,updateCustomer,format_date
    };
  },
};
</script>

