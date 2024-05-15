<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ store.count }}
    <button @click="store.increment()">test</button>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
<script setup>
import { reactive, watchEffect, ref } from "vue";

const store = reactive({
  count: 0,
  increment() {
    this.count++
  }
})



watchEffect(() => {

})

function changeState() {
  state.count = Date.now();
}
</script>



<script>
function reactive(obj) {
  const target = { ...obj };

  const handler = {
    get(target, prop) {
      return target[prop];
    },
    set(target, prop, value) {
      target[prop] = value;
      render();
    },
  };

  const proxy = new Proxy(target, handler);


  function render() {
    document.writeln(proxy.time);
    document.close();
  }

  return proxy;
}

const state = reactive(
  {
    time: Date.now(),
    updateTime() {
      this.time = new Date.now()
    }
  }
);

window.state = state;
</script>