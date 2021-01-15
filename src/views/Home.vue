<template>
  <div class="home">
    <Header :username='name' v-model="InputData.condition">
      <template v-slot:message>
        <p>Let's enjoy programming!</p>
      </template>
    </Header>
    <p>condition : {{ InputData.condition }} </p>

    <Body @add="add1"></Body>

    <Body @add="add2"></Body>
    <p>total : {{ totalcount }} </p>
    <button @click="componentName = 'Header'">Header</button>
    <button @click="componentName = 'Body'">Body</button>
    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Body from '@/components/Body.vue'
export default {
  name: 'Home',
  components: {
    Header,
    Body
  },
  data () {
    return {
      name: 'kiyokiyo',
      count1: 0,
      count2: 0,
      totalcount: 0,
      componentName: 'Header',
      InputData: {
        condition: ''
      }
    }
  },
  methods: {
    add1 (count) {
      this.count1 = count
      this.totalcount = this.count1 + this.count2
    },
    add2 (count) {
      this.count2 = count
      this.totalcount = this.count1 + this.count2
    }
  }
}

</script>

<style scoped>
  p {
    color: green
  }

</style>
