<template>
  <div id="app" style="width: 100%; height: 100%" class="is-black">
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand has-background-danger is-fullwidth">
        <a
          class="navbar-item is-size-3 has-text-weight-bold has-text-white"
          href="https://sspai.com/post/60454"
          target="_blank"
        >
          九九扑克
        </a>
        <div class="buttons is-fullwidth`">
          <a class="button" @click="zero">
            <span class="icon is-small">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                height="16"
                width="10"
                viewBox="0 0 320 512"
              >
                <!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.-->
                <path
                  d="M0 192C0 103.6 71.6 32 160 32s160 71.6 160 160V320c0 88.4-71.6 160-160 160S0 408.4 0 320V192zM160 96c-53 0-96 43-96 96V320c0 53 43 96 96 96s96-43 96-96V192c0-53-43-96-96-96z"
                />
              </svg>
            </span>
          </a>
          <a
            class="button is-light"
            @click="alwaysOn"
            v-bind:disabled="isAlwaysOn"
          >
            <span class="icon is-small">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                height="16"
                width="12"
                viewBox="0 0 384 512"
              >
                <!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.-->
                <path
                  d="M272 384c9.6-31.9 29.5-59.1 49.2-86.2l0 0c5.2-7.1 10.4-14.2 15.4-21.4c19.8-28.5 31.4-63 31.4-100.3C368 78.8 289.2 0 192 0S16 78.8 16 176c0 37.3 11.6 71.9 31.4 100.3c5 7.2 10.2 14.3 15.4 21.4l0 0c19.8 27.1 39.7 54.4 49.2 86.2H272zM192 512c44.2 0 80-35.8 80-80V416H112v16c0 44.2 35.8 80 80 80zM112 176c0 8.8-7.2 16-16 16s-16-7.2-16-16c0-61.9 50.1-112 112-112c8.8 0 16 7.2 16 16s-7.2 16-16 16c-44.2 0-80 35.8-80 80z"
                />
              </svg>
            </span>
          </a>
        </div>
      </div>
    </nav>
    <section class="section pt-4">
      <div class="container">
        <div class="columns is-mobile is-variable is-1 is-centered">
          <div
            class="column is-half has-text-centered"
            style="font-size: 9rem !important; font-weight: 800; hsl(0, 0%, 100%)"
            :class="{
              'has-text-danger': isDanger,
              'has-text-white': !isDanger,
            }"
          >
            {{ counter }}
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-6 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(3)"
            >
              +3
            </button>
          </div>
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-6 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(4)"
            >
              +4
            </button>
          </div>
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-6 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(5)"
            >
              +5
            </button>
          </div>
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-6 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(6)"
            >
              +6
            </button>
          </div>
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-6 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(9)"
            >
              +9
            </button>
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-5 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(-10)"
            >
              -10
            </button>
          </div>
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-5 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(10)"
            >
              +10
            </button>
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-5 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(-20)"
            >
              -Q(20)
            </button>
          </div>
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-5 is-fullwidth is-danger is-outlined has-text-white"
              @click="plus(20)"
            >
              +Q(20)
            </button>
          </div>
        </div>
        <div class="columns is-mobile is-variable is-1">
          <div class="column">
            <button
              class="button is-black is-medium is-responsive is-size-5 is-fullwidth is-danger is-outlined has-text-white"
              @click="full"
            >
              K
            </button>
          </div>
        </div>
      </div>
      <div class="content pt-4 has-text-white is-size-5">
        <h3 class="has-text-white">简易规则</h3>
        <ul>
          <li>排除大小鬼和 2</li>
          <li>开局每人发 5 张手牌</li>
          <li>当玩家打出的牌会让计数大于 99 时，淘汰出局</li>
          <li>当玩家手牌为 0，淘汰出局</li>
          <li>
            <strong class="has-text-white has-text-warning"
              >3、4、5、6、9</strong
            >：增加对应的计数
          </li>
          <li>
            <strong class="has-text-white has-text-warning">10</strong
            >：增加或减少 10 计数
          </li>
          <li>
            <strong class="has-text-white has-text-warning">Q</strong
            >：增加或减少 20 计数
          </li>
          <li>
            <strong class="has-text-white has-text-warning">K</strong
            >：让计数变为 99
          </li>
          <li>
            <strong class="has-text-white has-text-warning">A</strong
            >：指定一名玩家，下个回合从这名玩家开始（不影响顺序）
          </li>
          <li>
            <strong class="has-text-white has-text-warning">7</strong
            >：指定一名玩家，你和他交换全部的剩余手牌（本回合不再抽牌）
          </li>
          <li>
            <strong class="has-text-white has-text-warning">8</strong>：改变顺序
          </li>
          <li>
            <strong class="has-text-white has-text-warning">J</strong
            >：指定一名玩家，随机抽取他的一张手牌加入你的手牌（本回合不再抽牌）
          </li>
        </ul>
        <p>
          <a
            class="has-text-weight-bold"
            href="https://sspai.com/post/60454"
            target="_blank"
            >简单好玩易上手，民间自制聚会桌游：《99死 /
            死线99（Deadline99）》</a
          >
        </p>
      </div>
    </section>
  </div>
</template>

<script>
import _ from "lodash";
import NoSleep from "@uriopass/nosleep.js";

var noSleep = new NoSleep();

export default {
  name: "App",
  data() {
    return {
      isAlwaysOn: false,
      counter: 0,
    };
  },
  computed: {
    isDanger() {
      return this.$data.counter >= 90;
    },
  },
  methods: {
    plus: _.debounce(
      function (n) {
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
        trailing: false,
      }
    ),
    full() {
      this.$data.counter = 99;
    },
    zero() {
      this.$data.counter = 0;
    },
    alwaysOn: _.debounce(
      function () {
        if (this.$data.isAlwaysOn) {
          return;
        }

        this.$data.isAlwaysOn = true;
        noSleep.enable();
      },
      250,
      {
        leading: true,
        trailing: false,
      }
    ),
  },
};
</script>


