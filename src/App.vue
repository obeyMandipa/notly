<template>
    <header>
        
    </header>

    <main>
        
        <div class="h-[540px] w-[500px]  p-2 m-auto flex flex-col space-y-2 bg-red-400  p-4" >
            <div class="flex space-x-2">
                <input type="text" placeholder="Title" class="h-[50px] w-[360px] border border-black p-2 text-[18px] rounded-xl" v-model="title">
                <div class="icons h-[50px] w-[130px] flex justify-between ">
                    <img src="" alt="" class="w-[48px] h-[48px] bg-gray-400 rounded-full">
                    <img src="" alt="" class="w-[48px] h-[48px] bg-gray-400 rounded-full">
                </div>
            </div>
            <div class="">
                <textarea name="" id="" class="resize-none border border-black text-[18px] w-[470px] h-[380px] rounded-xl p-4" v-model="notes"></textarea>
            </div>
           <button @click="save()" class="bg-[#c4f5d3] hover:bg-[#095721] hover:text-white w-[50px] h-[50px] rounded-full text-center">Save</button>
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

    Methods: {
        async save() {
            console.log('working')
            const {data, error} = await supabase.from('Notes').insert('Title', 'Note')

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
