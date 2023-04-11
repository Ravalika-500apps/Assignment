<template>
    <div>
        <span v-html="html"> </span>
       <div v-html="root"></div>
       <div v-html="test"></div>
       
    </div>
</template>
<script setup="ts">

import { parse } from 'node-html-parser';
 
const html = parse('<!doctype html><html><body onload="alert(\'Hii Everyone\')">Mountain</body></html>');
const root = parse('<html><img width="570" src="https://www.w3schools.com/images/picture.jpg" alt="Mountain"></iframe></html>');


</script>