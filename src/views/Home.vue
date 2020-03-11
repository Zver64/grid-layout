<template>
  <div class="home">
    <div class="home__nav">
      <ul class="home__nav-list">
        <li class="home__nav-item">
          <button
            class="tag tag_purple"
            :class="disabled('travel')"
            @click="toggleTag('travel')"
          >
            Travel
          </button>
        </li>
        <li class="home__nav-item">
          <button
            class="tag tag_orange"
            :class="disabled('explorers')"
            @click="toggleTag('explorers')"
          >
            Explorers
          </button>
        </li>
        <li class="home__nav-item">
          <button
            class="tag tag_green"
            :class="disabled('nature')"
            @click="toggleTag('nature')"
          >
            Nature
          </button>
        </li>
        <li class="home__nav-item">
          <button
            class="tag tag_green"
            :class="disabled('сельское хозяйство')"
            @click="toggleTag('сельское хозяйство')"
          >
            Сельское хозяйство
          </button>
        </li>
        <li class="home__nav-item">
          <button
            class="tag tag_orange"
            :class="disabled('корма')"
            @click="toggleTag('корма')"
          >
            Корма
          </button>
        </li>
        <li class="home__nav-item">
          <button
            class="tag tag_cerulean"
            :class="disabled('science')"
            @click="toggleTag('science')"
          >
            Science
          </button>
        </li>
      </ul>
    </div>
    <div class="home__content">
      <el-grid :filter="filtered">
        <el-grid-item :tags="['travel']">
          <template v-slot:image>
            <img src="/beach.jpg" alt="beach" />
          </template>
          <template v-slot:title>
            <h3>Robot’s Penguin Disguise Keeps Birds</h3>
          </template>
          Figuring out how our brains work is key to understanding
        </el-grid-item>
        <el-grid-item :cols="2" :tags="['explorers']">
          <template v-slot:title>
            <h3>
              5 Things We Learned From X-Men: Days of Future Past
            </h3>
          </template>
          <template v-slot:image>
            <img src="/man.jpg" alt="man" />
          </template>
          Peter Dinklage’s porn ‘tache, Jennifer Lawrence’s brilliance and more.
          Some (tiny) spoilers ahead
        </el-grid-item>
        <el-grid-item
          more
          link="https://google.com"
          colored
          :tags="['science']"
          center
        >
          <template v-slot:title>
            <h3>
              14 Things Men Should Never Wear After 30
            </h3>
          </template>
          Light a bonfire in the garden, and step bravely into your best-dressed
          decade
        </el-grid-item>
        <el-grid-item :tags="['сельское хозяйство', 'корма']">
          <template v-slot:title>
            <h3>
              Комбикорма для уток и свиней оптом
            </h3>
          </template>
          Наши корма дают +20% к приросту массы в год
        </el-grid-item>
        <el-grid-item :tags="['explorers']">
          <template v-slot:image>
            <img src="/beach.jpg" alt="" />
          </template>
          <template v-slot:title>
            <h3>
              Stunning Changes Along Colorado River
            </h3>
          </template>
          Lake Powell offering kayakers new channels to explore
        </el-grid-item>
        <el-grid-item :tags="['travel']" :rows="2" center colored more>
          <template v-slot:title>
            14 Things Men Should Never Wear After 30
          </template>
          Light a bonfire in the garden, and step bravely into your best-dressed
          decade
        </el-grid-item>
        <el-grid-item :tags="['nature']">
          <template v-slot:image>
            <img src="/beach.jpg" alt="" />
          </template>
          <template v-slot:title>
            <h3>
              Offbeat Portraits Give Stars a New Turn
            </h3>
          </template>
          I whipped the Scotch tape from my pocket and said
        </el-grid-item>
        <el-grid-item :tags="['explorers']">
          <template v-slot:image>
            <img src="/beach.jpg" alt="" />
          </template>
          <template v-slot:title>
            <h3>
              Must See Places of the New Year
            </h3>
          </template>
          Whether it’s India’s literary hub or mountain majesty
        </el-grid-item>
        <el-grid-item :tags="['science']">
          <template v-slot:image>
            <img src="/beach.jpg" alt="" />
          </template>
          <template v-slot:title>
            <h3>
              Robot’s Penguin Disguise Keeps Birds
            </h3>
          </template>
          Figuring out how our brains work is key to understanding
        </el-grid-item>
        <el-grid-item :tags="['travel']">
          <template v-slot:image>
            <img src="/beach.jpg" alt="" />
          </template>
          <template v-slot:title>
            <h3>
              Stunning Video Reveals Invisible CO2
            </h3>
          </template>
          A NASA visualization shows the swirling gas
        </el-grid-item>
      </el-grid>
    </div>
  </div>
</template>

<script>
import ElGrid from '@/components/el-grid'
import ElGridItem from '@/components/el-grid-item'
export default {
  name: 'Home',
  components: {
    ElGrid,
    ElGridItem
  },
  data() {
    return {
      filter: {
        travel: true,
        explorers: true,
        nature: true,
        корма: true,
        'сельское хозяйство': true,
        science: true
      }
    }
  },
  methods: {
    toggleTag(tag) {
      this.$set(this.filter, tag, !this.filter[tag])
    },
    disabled(tag) {
      return { disabled: !this.filter[tag] }
    }
  },
  computed: {
    filtered() {
      return Object.keys(this.filter).filter(item => this.filter[item])
    }
  },
  mounted() {}
}
</script>
<style lang="scss">
.home {
  &__nav {
    padding: 12px 0;
    &-list {
      list-style: none;
      padding: 0;
      margin: 0;
      display: flex;
      overflow: auto;
      max-width: 100%;
    }
    &-item {
      padding-right: 20px;
      &:last-child {
        padding-right: 0;
      }
    }
  }
}
.tag {
  display: inline-block;
  cursor: pointer;
  border-radius: 3px;
  color: var(--white);
  background-color: black;
  border: none;
  font-weight: 600;
  font-size: 11px;
  padding: 2px 5px;
  text-transform: uppercase;
  &.disabled {
    opacity: 0.5;
  }
  &_purple {
    background-color: var(--bluish-purple);
  }
  &_orange {
    background-color: var(--dull-orange);
  }
  &_green {
    background-color: var(--greenish);
  }
  &_cerulean {
    background-color: var(--cerulean);
  }
}
</style>
