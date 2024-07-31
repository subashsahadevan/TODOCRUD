<template>
    <div id="default-modal" tabindex="-1" aria-hidden="true"
            class=" overflow-y-auto flex overflow-x-hidden fixed top-0 right-0 left-0 z-50 justify-center items-center w-full md:inset-0 h-[calc(100%-1rem)] max-h-full"
            v-show="openeditModal" >
            <div class="relative p-4 w-full max-w-2xl max-h-full">
                <div class="relative bg-white rounded-lg shadow  p-5">

                    <div>
                        <h3>Edit task details</h3>
                        <!-- {{ userDetails }} -->
                        <div class="mb-5">
                            <label for="base-input" class="block mb-2 text-sm font-medium text-gray-900">Name</label>
                            <input type="text" id="base-input"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5  dark:border-gray-600  dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                v-model="userDetails.name">
                        </div>
                        <!-- <input type="text" placeholder="Name of Task" v-model="name"> -->
                        <label for="message" class="block mb-2 text-sm font-medium text-gray-900 ">Description</label>
                        <textarea id="message" rows="4"
                            class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500  dark:border-gray-600 dark:focus:ring-blue-500 dark:focus:border-blue-500"
                            placeholder="Description..." v-model="userDetails.description"></textarea>
                        <!-- <textarea name="" id="" cols="30" rows="10" placeholder="Description" v-model="description">

                        </textarea> -->
                        <!-- <select v-model="assignto">
                            <option value="Subash Sahadevan">Subash Sahadevan</option>
                            <option value="Manu John">Manu John</option>
                            <option value="Anugraha S">Anugraha S</option>
                        </select> -->
                        <label for="countries" class="block mb-2 text-sm font-medium text-gray-900 ">Assign a
                            user</label>
                        <select id="countries"
                            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5  dark:border-gray-600   dark:focus:ring-blue-500 dark:focus:border-blue-500"
                            v-model="userDetails.assignto">

                            <option value="Subash Sahadevan">Subash Sahadevan</option>
                            <option value="Manu John">Manu John</option>
                            <option value="Anugraha S">Anugraha S</option>
                        </select>
                        <label for="countries" class="block mb-2 text-sm font-medium text-gray-900 ">Status</label>
                        <select id="countries"
                            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5  dark:border-gray-600   dark:focus:ring-blue-500 dark:focus:border-blue-500"
                            v-model="userDetails.status">

                            <option value="pending">Pending</option>
                            <option value="active">Active</option>
                        </select>
                    </div>
                    <div class="flex items-center p-4 md:p-5 border-t border-gray-200 rounded-b dark:border-gray-600">
                        <button data-modal-hide="default-modal" type="button"
                            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                            @click="handleupdateTaksSubmit">
                            Submit</button>
                        <button data-modal-hide="default-modal" type="button"
                            class="py-2.5 px-5 ms-3 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
                            @click="cancelModal">Close</button>
                    </div>
                </div>
            </div>
        </div>
</template>
<script>
export default {
    props:['editUserdata','openEditModal','cancelModal'],
    computed:{
        openeditModal: function (){
            return this.openEditModal
        },
        userDetails:function (){
            return this.editUserdata
        },
    },
    data(){
        return{
            
        }
    },
    methods:{
        updateData(){

        },
        cancelModal(){
            this.$emit('cancelModal')
        },
        handleupdateTaksSubmit(){

        }
    }

}
</script>