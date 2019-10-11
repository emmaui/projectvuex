<template lang="pug">
  #app
    img(src="./assets/logo.png" width="46")
    br
    //div
      //- h3(v-for="todos in $store.state.todos") {{todos}}
      h3(v-for="todos in todos") {{todos}}
      //- h3(v-for="todos in todos") {{todos.title}}
    button(@click="setTodos(['Amy','Tom','Peter'])") Update Todos
    button(@click="loadTodos") Load Todos
    br
    router-link(to="/test") To Page Test
    br
    router-link(to="/user/frank") To Page Frank
    br
    router-link(to="/user/lisa") To Page Lisa
    br
    router-link(to="/user/id/2") user 2
    transition(name="page" mode="out-in")
      router-view(:key="$route.path")
</template>

<script>
import{mapState,mapMutations,mapActions} from 'vuex'

export default {
  name: 'App',
  computed: {
    ...mapState(['todos'])
  },
  mounted(){
    // this.setTodos(['a','b','c'])
    this.loadTodos()
  },
  methods: {
    ...mapMutations(['setTodos']),
    ...mapActions(['loadTodos'])
  }
}
</script>

<style lang="sass">
#app 
  font-family: 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  margin-top: 60px
.page-enter-active,.page-leave-active
  transition: 0.5s
.page-enter,.page-leave-to
  opacity: 0
</style>
