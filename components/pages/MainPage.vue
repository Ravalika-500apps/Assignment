<template>
    <div>
      <PagesListPage
        :pageData="pageData"
        @deleteRecord="deletePage"
        @prefillData="prefillData"
      ></PagesListPage>
      <div>
        <PagesAddPage
          :selectedPage="selectedPage"
          @add-page="addPage"
        ></PagesAddPage>
        <PagesEditPage
          v-if="show"
          :key="renderEdit"
          :pageData="pageData.data._rawValue"
          :pageObj="pageObj"
          @updatePge="updatePge"
        ></PagesEditPage>
      </div>
    </div>
  </template>
  <script setup lang='ts'>
  import { ref } from "vue";
  
  // for getting data from get call
  const pageData = await useAuthLazyFetch(
    "https://v1-orm-lib.mars.hipso.cc/api/pages/?offset=0&limit=100&sort_column=id&sort_direction=desc",
    {}
  );
  
  // Declaring the variables
  const renderEdit = ref(0);
  const page = ref(pageData.data._rawValue);
  
  const pageObj = ref({});
  const show = ref(false);
  
  // add  fields
  const selectedPage = ref({
    name: "",
   category:"",
   page_html: null,
  page_css: null,
    
  });
  
  // add the Page
  const addPage = async (data: object) => {
   
    const postPrefs = {
      body: JSON.stringify(data),
    };
    // post call for adding page
    useAuthLazyFetchPost(
      "https://v1-orm-lib.mars.hipso.cc/api/pages/",
      postPrefs
    );
    page.value.unshift(data);
  };
  
  //edit the builder
  
  const prefillData = (data: object) => {
   
    show.value = true;
    pageObj.value = data;
    renderEdit.value++;
  };
  const updatePge = async (data: Object) => {
    
    const putOptions = {
      body: JSON.stringify(data),
    };
    await useAuthLazyFetchPut(
      `https://v1-orm-lib.mars.hipso.cc/api/pages/${data.uid}`,
      putOptions
    );
    getCall(data.uid)
  };
  
//   // delete the page
   const deletePage = (data: object) => {
   
    const deleteOptions = {
      body: JSON.stringify(data),
    };
    useAuthLazyFetchDelete(
      `https://v1-orm-lib.mars.hipso.cc/api/pages/${data.uid}`,
      deleteOptions
    );
    getCall(data.uid)
  };
  
  //get call through UID
   async function  getCall (data:any){
   await useAuthLazyFetch(`https://v1-orm-lib.mars.hipso.cc/api/pages/${data.uid}`,{})
  }
  </script>