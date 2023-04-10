<template>
  
  <table class="min-w-full divide-y divide-gray-300">
              <thead>
                <tr>
                  <th
                    scope="col"
                    class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                  >
                    Name
                  </th>
                  <th
                    scope="col"
                    class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                  AGE
                  </th>
                  <th
                    scope="col"
                    class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                    DATE OF dateofBirth
                  </th>
                  <th
                    scope="col"
                    class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                  >
                   DESIGNATION
                  </th>
                  <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-0">
                    <span class="sr-only">Edit</span>
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200">
                <tr v-for="(row, index) in project" :key="`item-${index}`">
                  <td v-for="(field, index) in fields" :key="`row-${index}`"
                  class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium sm:pl-0">
             {{ row[field] }}
                 <div class="flex" v-if="field=='actions'">
             <TrashIcon class="w-7 m-3" @click="emitData(row, index, 'delete')" />
              <PencilSquareIcon class="w-7 m-3" @click="emitData(row, index, 'edit')" />
            </div>
              </td>
                  <td
                    class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                  >
                    <button href="#" class="text-indigo-600 hover:text-indigo-900 mr-4" @click="emits('showEdit',person)">
                      Edit
                    </button>
                    <button href="#" class="text-indigo-600 hover:text-indigo-900" @click="emits('delete',person)">
                      Delete
                    </button>
                  </td>
                </tr>
              </tbody>
            </table>
                     
     <TransitionRoot appear :show="openModal" as="template">
      <Dialog as="div" class="relative z-10">
        <TransitionChild
          as="template"
          enter="duration-300 ease-out"
          enter-from="opacity-0"
          enter-to="opacity-100"
          leave="duration-200 ease-in"
          leave-from="opacity-100"
          leave-to="opacity-0"
        >
          <div class="fixed inset-0 bg-black bg-opacity-25" />
        </TransitionChild>
  
        <div class="fixed inset-0 overflow-y-auto">
          <div
            class="flex min-h-full items-center justify-center p-4 text-center"
          >
            <TransitionChild
              as="template"
              enter="duration-300 ease-out"
              enter-from="opacity-0 scale-95"
              enter-to="opacity-100 scale-100"
              leave="duration-200 ease-in"
              leave-from="opacity-100 scale-100"
              leave-to="opacity-0 scale-95"
            >
              <DialogPanel
                class="w-full max-w-md transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all"
              >
                
                <div v-if="edit">
                  
                </div>
                <div v-if="deleteProject">
                    <p>do you want to delete?</p>
                    <div class="mt-10 flex">
        <button
          type="submit"
          @click="openModal=false, emit('emitData', { note: $event, value: 'delete',index:editIndex })"
          class="block mr-2 rounded-md bg-indigo-600 px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
        >
          yes
        </button>
  
        <button
          type="submit"
          @click="closeModal"
          class="block rounded-md bg-indigo-600 px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
        >
          no
        </button>
      </div>
                </div>
              </DialogPanel>
            </TransitionChild>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>



</template>
<script setup lang="ts">
import {
  TransitionChild,
  DialogPanel,
  TransitionRoot,
  Dialog,
} from "@headlessui/vue";
import { TrashIcon, PencilSquareIcon } from "@heroicons/vue/24/outline";
const fields = ref([
   "age",
  "gender",
  "dateofBirth",
  "designation",
  "actions",
]);
const emit = defineEmits(["emitData"]);
const props = defineProps({
  project: { type: Array, required: true },
});


const edit = ref(false)
const deleteProject = ref(false)
const openModal=ref(false)

</script>