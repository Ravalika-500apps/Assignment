<template>
    <div>
       <CollectionList :detailsData="users" />
       <CollectionAdd></CollectionAdd>
    </div>
</template>


<script setup lang="ts">


const users = await useAuthLazyFetch("https://v1-orm-emc2-messaging.mars.hipso.cc/user-prefs/")
console.log("userrssss",users)

const editTemplate = (data:any) => {
   const editOptions = {
    method: "PUT",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiNmZlZDJiYTgwYThkNGM0MjlhZGZiOGQ1ZTZmZTY0ODAiLCJkIjoiMTY4MDA4NCIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzk3Mjl9.5cJkrudAvTWoVRigTNcfQ321W_lOyMm-xsb9rMxuVBE`,
  },
}
const editTemplateData = useAuthLazyFetchPut (
    `https://v1-orm-lib.mars.hipso.cc/email-templates/${data}`,
editOptions
)
    }


</script>