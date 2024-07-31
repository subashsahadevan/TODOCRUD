<template>
    <div>
        <div class=" mt-10 flex justify-end items-center p-5">
            <button class=" text-white bg-green-700 rounded px-3 py-2"> + Add Task</button>
        </div>
        <div >
            <input type="text" placeholder="Name of Task" v-model="name">
            <textarea name="" id="" cols="30" rows="10" placeholder="Description" v-model="description">

            </textarea>
            <select v-model="assignto">
                <option value="Subash Sahadevan">Subash Sahadevan</option>
                <option value="Manu John">Manu John</option>
                <option value="Anugraha S">Anugraha S</option>
            </select>
            <select name="" id="" v-model="status">
                <option value="pending">Pending</option>
                <option value="active">Active</option>
            </select>
            <button @click="handleAddTaksSubmit">Submit</button>
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
                    </tr>
                </thead>
                <tbody>
                    <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700" v-for="task in todos" :key="task">
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
                                class="bg-red-100 text-red-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded dark:bg-red-900 dark:text-red-300" v-if="task.status === 'pending'">Pending</span>
                            <span
                                class="bg-green-100 text-green-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded dark:bg-green-900 dark:text-green-300" v-else>Active</span>
                        </td>
                        <td class="px-6 py-4">
                            31/07/2024
                        </td>
                        <td class="px-6 py-4">
                            31/07/2024
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
        <!-- <div id="default-modal" tabindex="-1" aria-hidden="true"
            class="hidden overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 justify-center items-center w-full md:inset-0 h-[calc(100%-1rem)] max-h-full">
            <div class="relative p-4 w-full max-w-2xl max-h-full">
                <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">

                    <div class="flex items-center justify-between p-4 md:p-5 border-b rounded-t dark:border-gray-600">
                        <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                            Terms of Service
                        </h3>
                        <button type="button"
                            class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ms-auto inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white"
                            data-modal-hide="default-modal">
                            <svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none"
                                viewBox="0 0 14 14">
                                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"
                                    stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6" />
                            </svg>
                            <span class="sr-only">Close modal</span>
                        </button>
                    </div>

                    <div class="p-4 md:p-5 space-y-4">
                        <p class="text-base leading-relaxed text-gray-500 dark:text-gray-400">
                            With less than a month to go before the European Union enacts new consumer privacy laws for
                            its citizens, companies around the world are updating their terms of service agreements to
                            comply.
                        </p>
                        <p class="text-base leading-relaxed text-gray-500 dark:text-gray-400">
                            The European Union’s General Data Protection Regulation (G.D.P.R.) goes into effect on May
                            25 and is meant to ensure a common set of data rights in the European Union. It requires
                            organizations to notify users as soon as possible of high-risk data breaches that could
                            personally affect them.
                        </p>
                    </div>

                    <div class="flex items-center p-4 md:p-5 border-t border-gray-200 rounded-b dark:border-gray-600">
                        <button data-modal-hide="default-modal" type="button"
                            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">I
                            accept</button>
                        <button data-modal-hide="default-modal" type="button"
                            class="py-2.5 px-5 ms-3 text-sm font-medium text-gray-900 focus:outline-none bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:ring-gray-100 dark:focus:ring-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700">Decline</button>
                    </div>
                </div>
            </div>
        </div> -->

    </div>


</template>

<script>
export default {
    data(){
        return{
            todos:[],
            name:'',
            description:'',
            assignto:'',
            status:'',
            openModal:false,
        }
    },
    methods:{
        handleAddTaksSubmit(){
            const task = {
                name:this.name,
                description:this.description,
                assignto:this.assignto,
                status:this.status,
            }
            console.log(task)
            this.todos.push(task);
            this.name = '';
            this.description = '';
            this.assignto = '';
            this.status = '';
        }
    }
}
</script>