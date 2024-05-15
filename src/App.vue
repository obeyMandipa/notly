<template>
    <header>
        
    </header>

    <main>
        
        <div class="h-[540px] w-[500px]  p-2 m-auto flex flex-col space-y-2 bg-blue-100  p-4" >
            <div class="flex space-x-2">
                <input type="text" placeholder="Title" class="h-[50px] w-[400px] border border-black p-2 text-[18px] rounded-xl" v-model="title">
                <div class="icons h-[50px] w-[130px] flex justify-between ">
                   <button class="w-[48px] h-[48px] bg-white rounded-full flex justify-center items-center"><img src="@/assets/icons/notes.png" alt="" class="w-[30px] h-[30px] "></button> 
                   <button class="w-[48px] h-[48px] bg-white rounded-full flex justify-center items-center"><img src="@/assets/icons/settings.png" alt="" class="w-[30px] h-[30px] "></button> 
                </div>
            </div>
            <div class="">
                <textarea name="" id="" class="resize-none border border-black text-[18px] w-[470px] h-[380px] rounded-xl p-4" v-model="notes"></textarea>
            </div>
            <div class="flex justify-between "> 
                <button @click="save" class="w-[50px] h-[50px] bg-[#ffffff] rounded-full flex justify-center items-center "><img src="@/assets/icons/save.png" alt="" class="w-[30px] h-[30px]"> </button>
                <button @click="save" class="w-[50px] h-[50px] bg-[#ffffff] rounded-full flex justify-center items-center "><img src="@/assets/icons/pin.png" alt="" class="w-[28px] h-[28px]"> </button>

            </div>
        </div>
        

    </main>
</template>

<script>
import { supabase } from '@/lib/supabaseClient'


export default {
    data() {
        return{
            title: '',
            notes: '',
        };
    },

    methods: {
        async save() {
            const { data, error} = await supabase.from('Notes').insert([{Title: this.title, Note: this.notes}])

            if(error){
                console.log(error, 'insertion was not successful')
            }
            else{
                console.log(data)
            }

        }
    }



}

</script>

<style scoped>
/* main{
    background-color: #c4f5d3;
} */

</style>
