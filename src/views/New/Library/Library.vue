<template>
  <div class="habit">
    <!-- 新建说明 -->
    <section>
      <p>
        您可以从习惯库中挑选一个习惯,也可以新建一个新的习惯。
      </p>
    </section>
    <!-- 新建习惯 -->
    <section>
      <h4>自定义习惯</h4>
      <van-cell value="自定义习惯">
        <icon name="diy" slot="icon" />
      </van-cell>
    </section>
    <!-- 习惯库 -->
    <section>
      <h4>从库中挑选习惯</h4>
      <van-list>
        <router-link v-for="item in habitLibrary" :key="item.id" :to="{path:'habit',query:{id:item.id}}">
          <van-cell :value="item.title">
            <icon :name="item.name" slot="icon" />
          </van-cell>
        </router-link>
      </van-list>
    </section>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { List, Cell } from 'vant';

import config from '@/config';

@Component({
  components: {
      [List.name]: List,
      [Cell.name]: Cell,
  },
})
  export default class Library extends Vue {
    private title ?: string;
    private habitLibrary: object[];
    private data() {
      return {
        title: this.$route.name,
        habitLibrary: (config as any).habitLibrary,
      }
    }

    private onClickLeft() {
      this.$router.go(-1);
    }
  }
</script>

<style src="./style.scss" lang="scss" scoped>

</style>