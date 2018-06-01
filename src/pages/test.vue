<template>
  <div class="test">
    <p><a @click="showModal" style="cursor: pointer;">Click this to show Modal</a></p>
    <router-link to="/test/test1">前往test1页面</router-link>

    <transition
      name="custom-classes-transition"
      enter-active-class="animated tada"
      leave-active-class="animated bounceOutRight"
      mode="out-in"
    >
      <router-view></router-view>
    </transition>

    <modal>
      <div class="test-modal">
        <h3>hello modal</h3>
      </div>
    </modal>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
import modal from '@/components/popup/modal.vue'
export default {
  name: 'test',
  components: {
    modal
  },
  data () {
    return {
      
    }
  },
  mounted() {
  },
  methods:{
    ...mapActions({
      showModal: 'popup/modal/showModal'
    }),
    testMessage() {
      let type = ['info', 'success', 'warning', 'error']
      let typeInt = parseInt(Math.random()*4)
      this.$message({
        type: type[typeInt],
        message:'操作提示'
      })
    },
    testNotify() {
      let type = ['info', 'success', 'warning', 'error']
      let typeInt = parseInt(Math.random()*4)
      this.$notify({
        title: '标题',
        message: '这是一条提示消息',
        type: type[typeInt]
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  display: inline-block;
  color: #42b983;
  padding: 0 10px;
}

.test-modal{
  background-color: #fff;
  padding: 50px 200px
}
</style>
