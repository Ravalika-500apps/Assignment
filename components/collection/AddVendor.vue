<template>
    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10" @close="open = false">
        <TransitionChild as="template" enter="ease-out duration-300" enter-from="opacity-0" enter-to="opacity-100" leave="ease-in duration-200" leave-from="opacity-100" leave-to="opacity-0">
          <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />
        </TransitionChild>
  
        <div class="fixed inset-0 z-10 overflow-y-auto">
          <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
            
           
            <TransitionRoot as="template" :show="open">
        <Dialog as="div" class="relative z-10" @close="open = false">
            
          <div class="fixed inset-0" />
  
          <div class="fixed inset-0 overflow-hidden">
            <div class="absolute inset-0 overflow-hidden">
              <div
                class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10"
              >
                <TransitionChild
                  as="template"
                  enter-from="translate-x-full"
                  enter-to="translate-x-0"
                  leave-from="translate-x-0"
                  leave-to="translate-x-full"
                >
                  <DialogPanel class="pointer-events-auto w-screen max-w-md">
                    <div
                      class="flex h-full flex-col divide-y divide-gray-200 bg-white shadow-xl"
                    >
                      <div
                        class="flex min-h-0 flex-1 flex-col overflow-y-scroll py-6"
                      >
                        <div class="px-4 sm:px-6">
                          <div>
                            <DialogTitle
                              class="text-base font-semibold leading-6 text-gray-900"
                              >Add Vendor</DialogTitle
                            >
                            <div>
      <label
        for="note"
        class="block text-sm font-semibold leading-6 text-gray-900"
        >name</label
      >
      <div class="mt-2.5">
        <input
          name="note"
          v-model="name"
          id="note"
          rows="4"
          class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>
    <div>
      <label
        for="note"
        class="block text-sm font-semibold leading-6 text-gray-900"
        >Category</label
      >
      <div class="mt-2.5">
        <input
          name="note"
          v-model="email"
          id="note"
          rows="4"
          class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>
    <div>
      <label
        for="note"
        class="block text-sm font-semibold leading-6 text-gray-900"
        >email</label
      >
      <div class="mt-2.5">
        <input
          name="note"
          v-model="category"
          id="note"
          rows="4"
          class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>
    <div>
      <label
        for="note"
        class="block text-sm font-semibold leading-6 text-gray-900"
        >industry</label
      >
      <div class="mt-2.5">
        <input
          name="note"
          v-model="industry"
          id="note"
          rows="4"
          class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>
    <div class="mt-10 flex">
      <button
        type="submit"
        @click="emits('cancel')"
        class="block mr-2 rounded-md bg-indigo-600 px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
      >
        cancel
      </button>
  
      <button
        type="submit"
        @click="addBuilder"
        class="block rounded-md bg-indigo-600 px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
      >
        save
      </button>
             </div>
                            <div>
                              
                            </div>
  
                            <div class="ml-3 flex h-7 items-center">
                              <button
                                type="button"
                                class="rounded-md bg-white text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500"
                                @click="open = false"
                              >
                                <span class="sr-only">Close panel</span>
                                <XMarkIcon aria-hidden="true" />
                              </button>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </DialogPanel>
                </TransitionChild>
              </div>
            </div>
          </div>
        </Dialog>
      </TransitionRoot>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { Dialog, DialogPanel, DialogTitle, TransitionChild, TransitionRoot } from '@headlessui/vue'
  import { CheckIcon } from '@heroicons/vue/24/outline'
  
  const open = ref(true)
  let name = ref("")
  let category = ref("")
  let email = ref("")
  let industry = ref("")
  const vendorDetails = ref({})
  const emits = defineEmits(["addData"])
  
  const add = () =>{
      console.log("add--->")
      vendorDetails.value = {name:name.value,category:category.value,email:email.value,industry:industry.value}
    
      open.value = false
      emits("addData",vendorDetails.value)
      console.log("add--->")
  }
  </script>