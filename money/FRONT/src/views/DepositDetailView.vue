<template>
    <div>
        {{ route.params.id }}
        <div v-for="depositdata in depositdatas" :key="depositdata.id">
            {{ depositdata.intr_rate }}
            {{ depositdata.intr_rate2 }}
            {{ depositdata.save_trm }}
        </div>
        <div>
            <RouterLink :to="{ name: 'FinView' }">[Back]</RouterLink>
        </div>
    </div>
</template> 

<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue';
import { RouterLink } from 'vue-router';
import { useRoute } from 'vue-router';
import { useCounterStore } from '@/stores/counter'

defineProps(['deposit']);

const store = useCounterStore()
const route = useRoute()
const depositdatas = ref(null)
onMounted(() => {
    console.log(store.API_URL)
    axios({
        method: 'get',
        url: `http://127.0.0.1:8000/fin/deposit-products/${route.params.id}/`,
    }) .then((res) => {
        depositdatas.value = res.data
        console.log(depositdatas.value)
        console.log(route.params)
    }) .catch(err => console.log(err))
})

</script>

<style scoped>

</style>