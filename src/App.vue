<template>
<div class="container grid-lg my-2 py-2">
<div class="card">
  <div class="card-header">
    <div class="h4">Todas as moedas</div>
  </div>
  <div class="card-body">
    <ListQuotes :quotes="quotes" />
  </div>
</div>
</div>
</template>

<script>
import { onMounted, reactive, toRefs } from 'vue'
import api from './services/api'
import ListQuotes from './components/ListQuotes'
export default {
  name: 'App',
  components: {ListQuotes},
   setup(){
    // ! ref fala que é reativo
    // let model = ref('teste')
    // ! mudar valor que que usar .value
    // model.value = "mudando valor"

    const data = reactive({
      quotes: {},
    })

    // ! traz dados assim que carregar a tela
    onMounted(async () => {
      const response = await api.all();
      data.quotes = response.data;
    });

    return {...toRefs(data)}
  }
}
</script>

<style>

</style>
