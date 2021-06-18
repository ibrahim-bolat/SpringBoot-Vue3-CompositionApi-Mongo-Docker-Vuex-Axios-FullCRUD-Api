<template>
  <div class="anasayfa">
      <div class="row">
        <div class="col col-sm-4">
          <div class="container">
          <customer-form />
          </div>
        </div>
        <div class="col col-sm-8">
          <div class="container">
          <customer-table />
          </div>
        </div>
      </div>
    <form-modal v-if="displayModal" @close-modal-event="hideModal(false)" />
  </div>
</template>
<script>
import CustomerForm from "@/components/customer/CustomerForm";
import CustomerTable from "@/components/customer/CustomerTable";
import FormModal from "@/components/customer/FormModal";
import {computed} from "vue"
import { useStore } from 'vuex'
export default {
  name: "Home",
  components: {
    CustomerForm,
    CustomerTable,
    FormModal,
  },
  setup() {
    const store = useStore();
    const hideModal=(bool)=>{
        store.dispatch('changeDisplayModal', bool)
       };
    const displayModal=computed(()=>{
        return store.getters.getDisplayModal
       });
    return{
      hideModal,displayModal
    }
  },

};
</script>
<style>
</style>
