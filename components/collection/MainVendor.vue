<template>
    <div>
      <div>
       <CollectionListVendor :vendorData="vendorData"  @show="addVendor" @showEdit="editVendor" @delete="deleteVendor"/>   
      </div>
      <div  v-if="show">
       <CollectionAddVendor v-if="show" @addData="addData" :key="renderAdd"/>
       </div>
       <div v-if="showData">
       <CollectionEditVendor v-if="showData"  :editInfo="editInfo"  @editData="editData" :key="renderEdit"/>
       </div>
  </div>

</template>

<script setup lang="ts">
import {ref} from "vue"

 // Declaring variables
const show = ref(false)
const showData = ref(false)
const renderEdit = ref(0)
const renderAdd = ref(0)
const editInfo = ref({})

 // Get all the vendors
const getOptions = {
  method: "GET",
  headers: {
      "Content-Type": "application/json",
      
     Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZTk3YTIxZjM4ZDc4NDgwYjlhYjdhOTI0M2Q0NjViNzgiLCJkIjoiMTY4MDA5NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODc4Mjd9.qFyxIJYJLihyxfui4QRMOLjJgwBr95z3N3lWRDz89ZU`,
  },
};

var vendorData = useAuthLazyFetch(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/?offset=0&limit=100&sort_column=id&sort_direction=desc",
  getOptions
);
console.log("vendorData--->",vendorData)

 // Add vendor 
const addData = (data:object) => {
    console.log("data in main--->",data,data.name)
    const postOptions = {
    body: {
      name: data.name,
      category: data.category,
      email: data.email,
      industry: data.industry,
      rating: 0,
     type: "Vendor",
      address: {
    street: "hiii",
    city: "hello",
    state: "data",
    country: "india",
    zip_code: "49638"
  },
    website: "string",
    status: 1,
     profile_id: "107"
    },
  };

  const addVendorData =  useAuthLazyFetchPost(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/",
    postOptions
  );
  
}


 // deleting the vendor based on uid 
   const deleteVendor = (data:any) => {
   const deleteOptions = {
    method: "DELETE",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZTk3YTIxZjM4ZDc4NDgwYjlhYjdhOTI0M2Q0NjViNzgiLCJkIjoiMTY4MDA5NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODc4Mjd9.qFyxIJYJLihyxfui4QRMOLjJgwBr95z3N3lWRDz89ZU`,
  },
}

const deleteTemplateData = useAuthLazyFetchDelete (
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/${data.name}`,
deleteOptions
)
    }

 // Open add vendor modal
const addVendor = (data) => {
  console.log('addVendor--->', show.value,data)
  show.value = data
  renderAdd.value++
  console.log('addVendor 2 --->', show.value)
}

 // Open the edit vendor modal
const editVendor = (data) => {
  console.log("editVendor----assdasdsda>",data)
        showData.value = true
        renderEdit.value++
        editInfo.value = data
    console.log("editVendor--->",data,renderEdit.value)
}
</script>