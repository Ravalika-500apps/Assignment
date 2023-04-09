<template>
    <div>
      <BuilderListBuilder
        :builderData="builderData"
        @deleteRecord="deleteBuilder"
        @prefillData="prefillData"
      ></BuilderListBuilder>
      <div>
        <BuilderAddBuilder
          :selectedBuilder="selectedBuilder"
          @add-builder="addBuilder"
        ></BuilderAddBuilder>
        <BuilderEditBuilder
          v-if="show"
          :key="renderEdit"
          :builderData="builderData.data._rawValue"
          :builderObj="builderObj"
          @updateBuilder="updateBuilder"
        ></BuilderEditBuilder>
      </div>
    </div>
  </template>
  <script setup lang='ts'>
  import { ref } from "vue";
  
  // for getting data from get call
  const builderData = await useAuthLazyFetch(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/?offset=0&limit=100&sort_column=id&sort_direction=desc",
    {}
  );
  
  // Declaring the variables
  const renderEdit = ref(0);
  const block = ref(builderData.data._rawValue);
  const getData = ref({});
  const builderObj = ref({});
  const show = ref(false);
  
  // add  fields
  const selectedBuilder = ref({
    name: "",
    email: "",
    phone_number: null,
    logo: null,
  });
  
  // add the builder
  const addBuilder = async (data: object) => {
    console.log("addddata-------->", data);
    const postPrefs = {
      body: JSON.stringify(data),
    };
    // post call for adding builder
    useAuthLazyFetchPost(
      "https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/",
      postPrefs
    );
    block.value.unshift(data);
  };
  
  //edit the builder
  
  const prefillData = (data: object) => {
   
    show.value = true;
    builderObj.value = data;
    renderEdit.value++;
  };
  const updateBuilder = async (data: Object) => {
    
    const putOptions = {
      body: JSON.stringify(data),
    };
    await useAuthLazyFetchPut(
      `https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/${data.uid}`,
      putOptions
    );
    getCall(data.uid)
  };
  
//   // delete the builder
   const deleteBuilder = (data: object) => {
   
    const deleteOptions = {
      body: JSON.stringify(data),
    };
    useAuthLazyFetchDelete(
      `https://v1-orm-gharpe.mercury.infinity-api.net/api/builder/${data.uid}`,
      deleteOptions
    );
    getCall(data.uid)
  };
  
  // get call through UID
   async function  getCall (data:any){
   await useAuthLazyFetch(`https://v1-orm-lib.mars.hipso.cc/api/blocks/${data}`,{})
  }
  </script>