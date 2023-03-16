<template>
    <div class="flex justify-center mt-5">
        <ul v-show="typedata.length" class="w-96  bg-gray-300" :class="winner ?  'bg-neutral-800' :  'bg-gray-300'">
            
            <div class="m-4 ">
                <div v-show="winner" class="text-white mt-4 mb-4">Top 3 Winner</div>
                <li  v-for="(item,index) in typedata" :key="index" class="bg-white">
                    <div v-if="item.name && item"  class="w-full border-2 border-neutral-100 border-opacity-100 py-4 dark:border-opacity-50 pl-4 mb-1">
                        <div >Student:  {{ item.name }}</div>
                        <div >Year : {{ item.year }} Room: {{ item.class }}</div>
                    </div>
                    <div v-if="item.title && item"  class="w-full border-2 border-neutral-100 border-opacity-100 py-4 dark:border-opacity-50 pl-4 mb-1">
                        <div >Title:  {{ item.title }}</div>
                        <div >Category : {{ item.category }} | {{ item.rating }} likes</div>
                    </div>
                    
                    <div v-if="item.winner && item"  class="w-full border-2 border-neutral-100 border-opacity-100 py-4 dark:border-opacity-50 pl-4 mb-1">
                        <div>{{ item.rank }} {{ item.winner }}</div>
                    </div>
                    
                </li>
            </div>
        </ul>
       
    </div>
    
</template>

<script>
import { computed } from "vue"
export default {
    props:['typedata'],
    setup(props){
        console.log(props.typedata)
        // const x = ref(props.test)
        const winner = computed(()=>{
            if(props.typedata.length>0 && props.typedata[0].winner){
                return true;
            }
            return false
        })
        return {winner}
    }
}
</script>