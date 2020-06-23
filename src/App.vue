<template>
  <div id="app">
    <nav
      class="navbar"
      role="navigation"
      aria-label="main navigation"
      style="background-color: #E45A6A;"
    >
      <div class="navbar-brand">
        <a class="navbar-item" href="https://sspai.com/post/60454" target="_blank">
          <h3 class="title is-3" style="color: white;">99POKER</h3>
        </a>
      </div>
    </nav>
    <section class="section" style="padding: 1rem 1.5rem;">
      <div class="container">
        <div class="columns">
          <div class="column" style="text-align: center; font-size: 9rem; font-weight: 600;">
            <span
              class="counter"
              :class="{ 'my-warning': isWarning}"
              @dblclick="restart"
            >{{counter}}</span>
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button style="height: 60px" class="button" @click="plus(3)">+3</button>
          </div>
          <div class="column">
            <button style="height: 60px" class="button" @click="plus(4)">+4</button>
          </div>
          <div class="column">
            <button style="height: 60px" class="button" @click="plus(5)">+5</button>
          </div>
          <div class="column">
            <button style="height: 60px" class="button" @click="plus(6)">+6</button>
          </div>
          <div class="column">
            <button style="height: 60px" class="button" @click="plus(9)">+9</button>
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button style="height: 60px" class="button is-info is-light" @click="plus(-10)">-10</button>
          </div>
          <div class="column">
            <button style="height: 60px" class="button is-info is-light" @click="plus(10)">+10</button>
          </div>
          <div class="column">
            <button style="height: 60px" class="button is-info is-light" @click="plus(-20)">-20</button>
          </div>
          <div class="column">
            <button style="height: 60px" class="button is-info is-light" @click="plus(20)">+20</button>
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button style="height: 60px" class="button is-warning is-light" @click="full">k</button>
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button
              style="height: 60px"
              class="button is-success is-light"
              onclick="alert('指定一名玩家，下个回合从这名玩家开始（不影响顺序）')"
            >A</button>
          </div>
          <div class="column">
            <button
              style="height: 60px"
              class="button is-success is-light"
              onclick="alert('指定一名玩家，你和他交换全部的剩余手牌（本回合不再抽牌）')"
            >7</button>
          </div>
          <div class="column">
            <button
              style="height: 60px"
              class="button is-success is-light"
              onclick="alert('改变顺序')"
            >8</button>
          </div>
          <div class="column">
            <button
              style="height: 60px"
              class="button is-success is-light"
              onclick="alert('指定一名玩家，随机抽取他的一张手牌加入你的手牌（本回合不再抽牌）')"
            >J</button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style>
html body #app {
  width: 100%;
  height: 100%;
}

button {
  width: 100%;
}

.my-warning {
  color: #e45a6a;
}
</style>

<script>
import _ from "lodash";

export default {
  name: "App",
  data() {
    return {
      counter: 0
    };
  },
  computed: {
    isWarning() {
      return this.$data.counter >= 90;
    }
  },
  methods: {
    plus: _.debounce(
      function(n) {
        let c = this.$data.counter + n;

        if (c > 99) {
          alert("超过 99 啦");
          return;
        }

        this.$data.counter = c < 0 ? 0 : c;
      },
      250,
      {
        leading: true,
        trailing: false
      }
    ),
    full() {
      this.$data.counter = 99;
    },
    restart() {
      this.$data.counter = 0;
    }
  }
};
</script>


