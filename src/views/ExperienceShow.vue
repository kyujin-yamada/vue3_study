<template>
    <section>
        <img :src="`/images/${experience.image}`"  :alt="experience.name" />
        <p>{{ experience.description }}</p>
    </section>
</template>
<script>
import { defineComponent } from 'vue'
import sourceData  from '../data.json'
export default defineComponent({
    props:{
        id: {type: Number, required: true,},
        experienceSlug: {type: String,  required: true,}
    },
    computed:{
        destination(){
            return sourceData.destinations.find(
                destination => destination.id === this.id
            );
        },
        experience(){
            return this.destination.experiences.find(
                experience => experience.slug === this.experienceSlug
            );
        }
    }
})
</script>