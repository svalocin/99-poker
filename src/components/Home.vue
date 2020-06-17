<template>
  <div style="width: 100%; height: 100%;">
    <nav style="background: #E45A6A;">
      <a href="/" class="brand">
        <span>
          <font style="vertical-align: inherit;">
            <font style="vertical-align: inherit;">99 扑克</font>
          </font>
        </span>
      </a>
    </nav>
    <div class="main">
      <div style="width: 100%; padding-bottom: 100%;">
        <span class="counter" :class="{ 'my-warning': isWarning}">{{counter}}</span>
      </div>
      <div>
        <div class="flex five">
          <div>
            <span>
              <button class="big default" @click="plus(3)">+3</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big default" @click="plus(4)">+4</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big default" @click="plus(5)">+5</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big default" @click="plus(6)">+6</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big default" @click="plus(9)">+9</button>
            </span>
          </div>
        </div>
        <div class="flex four">
          <div>
            <span>
              <button class="big success" @click="plus(-10)">-10</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big success" @click="plus(10)">+10</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big success" @click="plus(-20)">-Q</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big success" @click="plus(20)">+Q</button>
            </span>
          </div>
        </div>
        <div class="flex">
          <div>
            <span>
              <button class="big success" style="width: 100%;" @click="full">K</button>
            </span>
          </div>
        </div>
        <div class="flex four">
          <div>
            <span>
              <button class="big warning" onclick="alert('指定一名玩家，下个回合从这名玩家开始（不影响顺序）')">A</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big warning" onclick="alert('指定一名玩家，你和他交换全部的剩余手牌（本回合不再抽牌）')">7</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big warning" onclick="alert('改变顺序')">8</button>
            </span>
          </div>
          <div>
            <span>
              <button class="big warning" onclick="alert('指定一名玩家，随机抽取他的一张手牌加入你的手牌（本回合不再抽牌）')">J</button>
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  padding: 52.8px 24px 10px 24px;
}

button.default {
  background: white;
  color: black;
  border: 1px solid;
  height: 50px;
}

button.big {
  height: 60px;
}

.flex button {
  width: 100%;
}

.counter {
  width: 100%;
  height: 100%;
  text-align: center;
  font-size: 300px;
  line-height: initial;
  float: left;
}

.my-warning {
  color: #ff851b;
}
</style>

<script>
export default {
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
    plus(n) {
      let c = this.$data.counter + n;

      if (c > 99) {
        alert("超过 99 啦");
        return;
      }

      this.$data.counter = c < 0 ? 0 : c;
    },
    full() {
      this.$data.counter = 99;
    }
  }
};
</script>


