<template>
  <div
    class="el-grid-item"
    :style="{
      'grid-row-start': 'span ' + rows,
      'grid-column-start': 'span ' + cols
    }"
    :class="
      Object.assign(
        {
          'el-grid-item_center': center
        },
        itemClass()
      )
    "
  >
    <div
      class="el-grid-item__main"
      :class="{ 'el-grid-item__main_wide': wide }"
    >
      <div
        v-if="$slots.image"
        class="el-grid-item__img-box"
        :class="{ 'el-grid-item__img-box_wide': wide }"
      >
        <slot name="image" />
      </div>
      <div class="el-grid-item__content">
        <ul
          class="el-grid-item__tags"
          :class="{
            'el-grid-item__tags_static': wide || center || !$slots.image
          }"
          v-if="tags.length > 0"
        >
          <li v-for="tag in tags" :key="tag">
            <div class="tag" :class="tagClass(tag)">{{ tag }}</div>
          </li>
        </ul>
        <slot name="title" />
        <slot />
      </div>
    </div>
    <div class="el-grid-item__more" v-if="more">
      <a :href="link" class="btn">Read more</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'el-grid-item',
  props: {
    rows: {
      default: 1,
      type: Number
    },
    cols: {
      default: 1,
      type: Number
    },
    tags: {
      default() {
        return []
      },
      type: Array
    },
    more: {
      default: false,
      type: Boolean
    },
    colored: {
      default: false,
      type: Boolean
    },
    center: {
      default: false,
      type: Boolean
    },
    hidden: {
      default: false,
      type: Boolean
    },
    link: {
      default: '',
      type: String
    }
  },
  methods: {
    tagClass(tag) {
      const classes = {
        travel: 'tag_purple',
        explorers: 'tag_orange',
        nature: 'tag_green',
        'сельское хозяйство': 'tag_green',
        корма: 'tag_orange',
        science: 'tag_cerulean'
      }
      return classes[tag] || ''
    },
    itemClass() {
      if (!this.colored) return
      const classes = {
        travel: 'el-grid-item_purple',
        explorers: 'el-grid-item_orange',
        nature: 'el-grid-item_green',
        'сельское хозяйство': 'el-grid-item_green',
        корма: 'el-grid-item_orange',
        science: 'el-grid-item_cerulean'
      }
      return (
        { [classes[this.tags[0]]]: true, 'el-grid-item_colored': true } || {}
      )
    }
  },
  computed: {
    wide() {
      return this.$props.cols > 1
    }
  }
}
</script>

<style lang="scss">
.el-grid-item {
  display: flex;
  flex-direction: column;
  min-width: 230px;
  border-radius: var(--border-radius);
  padding: 20px;
  background-color: var(--white);
  position: relative;
  &_hidden {
    display: none;
  }
  &__content {
    color: var(--steel-grey);
    h3 {
      color: var(--charcoal-grey-two);
      font-size: 15px;
      margin-top: 1.5em;
      margin-bottom: 1em;
    }
  }
  &_colored {
    .el-grid-item__content {
      color: white;
      h3 {
        color: white;
      }
    }
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
  @include r(530) {
    grid-column-start: 1 !important;
  }
  &_center {
    justify-content: center;
    text-align: center;
  }
  &__main {
    &_wide {
      display: flex;
      flex-direction: row-reverse;
      @include r(530) {
        display: block;
        .el-grid-item__tags {
          position: absolute;
        }
      }
    }
  }
  &__img-box {
    margin: -20px -20px 0;
    flex-shrink: 0;
    max-height: 265px;
    display: flex;
    &_wide {
      margin: 0;
    }
    img {
      max-width: 100%;
      margin: 0 auto;
      height: auto;
      object-fit: cover;
    }
  }
  &__tags {
    position: absolute;
    top: 20px;
    left: 20px;
    padding: 0;
    list-style: none;
    margin: 0;
    &_static {
      position: static;
      margin-bottom: 15px;
    }
  }
  &__more {
    align-self: center;
    padding-top: 15px;
    .btn {
      padding: 5px 20px;
      border-radius: 20px;
      color: white;
      border: solid 1px rgba(#ededed, 0.2);
      background-color: transparent;
      cursor: pointer;
      text-decoration: none;
      display: inline-block;
    }
  }
}
</style>
