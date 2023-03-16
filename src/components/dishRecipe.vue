<template>
    <div class="flex justify-center">
        <div v-if="solution" class="w-96 mt-3 bg-gray-100 p-4">
            <ul>
                <div v-for="(items,row) in solution" :key=row class="flex bg-gray-100">
                    <li v-for="(item,index) in items" :key="index" class="ml-2 mr-2 ">
                        {{ item }}
                    </li>
                </div>
            </ul>
        </div>
    </div>
    

</template>

<script>
import { computed } from 'vue' 

export default {
    props:['recipes'],
    setup(props){
        const solution = computed(()=>{
            const ingredients = {}
            try{
                if(props.recipes.length >= 1 && props.recipes.length <=500){
                    for(const res of props.recipes){
                        if(res.length>=2 && res.length <=10){
                            for(let i =1; i<res.length;i++){
                                if(res[i].length >= 0 && res[i].length <= 50){
                                    const ingredient = res[i].charAt(0).toUpperCase()+res[i].slice(1);
            
                                    if(!(ingredient in ingredients)){
                                        ingredients[ingredient]=[];
                                    }
                                    //push dish into ingredients[] array
                                    console.log(res[0].charAt(0).toUpperCase()+res[i].slice(1))
                                    console.log(res[0])
                                    ingredients[ingredient].push(res[0].charAt(0).toUpperCase()+res[0].slice(1));
                                }else{
                                    throw new Error('name of recipe too long')
                                    
                                }
                            }
                        }else{
                            //error amount of recipe too few
                            throw new Error('amount of recipe too few or too many')
                            
                        }


                    }
                    const sortedIngredients = Object.keys(ingredients).sort();
                    const resultArr = [];
                    const arr = []
                    for(const item of sortedIngredients){
                        arr.push([item,...ingredients[item].sort()]);
                        
                    }

                    for(const item of arr){ 
                        if(item.length > 2){
                            resultArr.push(item)
                        }
                    }
                    return resultArr 
                }
                else{
                    throw new Error('too many dish or none')
                }
            }catch(error){
                console.error(error);
                return false;
            }
            
            

        })
        return {solution}
    }
}

</script>