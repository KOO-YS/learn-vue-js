<template>
  <div> 
      <!-- 컴포넌트 등록 -->
      <app-header v-bind:propsdata="str"
      v-on:renew="renewStr"></app-header>
      <header>app</header>
      <br>
      {{ str }}
  </div>
  <!-- 최상단 앨리먼트는 하나만 존재 가능(안으로만 확장) -->
  <!-- <div></div> 추가 불가능 -->
</template>

<script>
import appHeader from './components/AppHeader.vue';

export default {
  // 함수를 리턴하는 형식으로 진행해야한다
  data: function(){
    return {
      str: 'Props'
    }
  },
  // import한 컴포넌트 등록
  components: { 
    'app-header': appHeader
  },
  methods: {
    renewStr: function(){
      this.str = 'hi';
    }
  }
}
</script>

<style>

</style>