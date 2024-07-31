<template>
    <div>
        <div class=" mt-10 flex justify-end items-center p-5">
            <button class=" text-white bg-green-700 rounded px-3 py-2" @click="openAddTaskModal" :disabled="todos.length == 5"> + Add Task</button>
        </div>
        <div class="relative overflow-x-auto p-5">
            <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                <thead class="text-xs text-gray-700 uppercase bg-green-600 dark:bg-green-600 dark:text-white">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            Name
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Description
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Assign to
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Status
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Created At
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Updated At
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Action
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700" v-for="(task,index) in todos"
                        :key="task">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                            {{ task.name }}
                        </th>
                        <td class="px-6 py-4">
                            {{ task.description }}
                        </td>
                        <td class="px-6 py-4">
                            {{ task.assignto }}
                        </td>
                        <td class="px-6 py-4">
                            <span
                                class="bg-red-100 text-red-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded dark:bg-red-900 dark:text-red-300"
                                v-if="task.status === 'pending'">Pending</span>
                            <span
                                class="bg-green-100 text-green-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded dark:bg-green-900 dark:text-green-300"
                                v-else>Active</span>
                        </td>
                        <td class="px-6 py-4">
                            31/07/2024
                        </td>
                        <td class="px-6 py-4">
                            31/07/2024
                        </td>
                        <td class="px-6 py-4">
                            <button class=" px-3 py-2 bg-blue-600 text-white rounded mr-2" @click="editUser(task)">Edit</button>
                            <button class=" px-3 py-2 text-white bg-red-600 rounded" @click="deleteUser(task,index)">Delete</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div id="default-modal" tabindex="-1" aria-hidden="true"
            class=" overflow-y-auto flex overflow-x-hidden fixed top-0 right-0 left-0 z-50 justify-center items-center w-full md:inset-0 h-[calc(100%-1rem)] max-h-full"
            v-show="openModal" >
            <div class="relative p-4 w-full max-w-2xl max-h-full">
                <div class="relative bg-white rounded-lg shadow  p-5">

                    <div>
                        <h3>Add the task details</h3>
                        <div class="mb-5">
                            <label for="base-input" class="block mb-2 text-sm font-medium text-gray-900">Name</label>
                            <input type="text" id="base-input"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5  dark:border-gray-600  dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                v-model="name">
                        </div>
                        <!-- <input type="text" placeholder="Name of Task" v-model="name"> -->
                        <label for="message" class="block mb-2 text-sm font-medium text-gray-900 ">Description</label>
                        <textarea id="message" rows="4"
                            class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500  dark:border-gray-600 dark:focus:ring-blue-500 dark:focus:border-blue-500"
                            placeholder="Description..." v-model="description"></textarea>
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
                            v-model="assignto">

                            <option value="Subash Sahadevan">Subash Sahadevan</option>
                            <option value="Manu John">Manu John</option>
                            <option value="Anugraha S">Anugraha S</option>
                        </select>
                        <label for="countries" class="block mb-2 text-sm font-medium text-gray-900 ">Status</label>
                        <select id="countries"
                            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5  dark:border-gray-600   dark:focus:ring-blue-500 dark:focus:border-blue-500"
                            v-model="status">

                            <option value="pending">Pending</option>
                            <option value="active">Active</option>
                        </select>
                    </div>
                    <div class="flex items-center p-4 md:p-5 border-t border-gray-200 rounded-b dark:border-gray-600">
                        <button data-modal-hide="default-modal" type="button"
                            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                            @click="handleAddTaksSubmit">
                            Submit</button>
                        <button data-modal-hide="default-modal" type="button"
                            class="py-2.5 px-5 ms-3 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700"
                            @click="cancelModal">Close</button>
                    </div>
                </div>
            </div>
        </div>
        <editTodo :editUserdata="editUserdata" :openEditModal="openEditModal" @cancelModal="cancelModal($event)" @updateUserdetails="updateUserdetails($event)"/>
    </div>


</template>

<script>
import editTodo from './editTodo.vue';
export default {
    components:{
        editTodo
    },
    data() {
        return {
            todos: [],
            name: '',
            description: '',
            assignto: '',
            status: '',
            openModal: false,
            editUserdata:[],
            openEditModal:false
        }
    },
    methods: {
        handleAddTaksSubmit() {
            const task = {
                name: this.name,
                description: this.description,
                assignto: this.assignto,
                status: this.status,
            }
            console.log(task)
            this.todos.push(task);
            this.name = '';
            this.description = '';
            this.assignto = '';
            this.status = '';
            this.openModal = false;
        },
        openAddTaskModal() {
            this.openModal = true;
        },
        cancelModal() {
            this.openModal = false;
        },
        editUser(task){
            this.editUserdata = task;
            this.openEditModal = true;
        },
        deleteUser(task,index){
            this.todos.splice(index,1)
            // console.log(task +'task');
            // console.log(index+'index');
            
        },
        cancelModal(){
            this.openEditModal = false;
        }
    }
}
</script>