<template>
  <section class="our-work">
    <div class="container">
      <h3 class="is-heading">Simple and clean interface</h3>
      <p class="info">Tamiat CMS offers easy and simple UI for its users when creating or editing their content, as well as an intuitive way of creating fully customisable pages for anything a developer could need</p>
      <ul class="grid" v-if="works">
        <li v-for="work in works" :key="work['.key']" :class="[ work.title === 'Work 3' ? 'small' : 'large']" :style="{'background-image': `url(${work.img})`}"></li>
      </ul>
    </div>
  </section> 
</template>

<script>
import contentFetch from '@/admin/mixins/contentFetch'
import { contentsRef } from '@/admin/firebase_config'

export default {
  name: 'section-work',
  mixins: [contentFetch],
  firebase: {
    contents: contentsRef
  },
  computed: {
    works () {
      return this.getContentsByType('Works')
    }
  }//  
}
</script>

<style lang="scss" scoped>
@import '@/app/styles/index.scss';

/*--------------------
       Our Work Section
  ---------------------*/

.our-work {
  background-color: #fff;
  .is-heading {
    color: $color-orange;
  }
  .grid {
    padding: 60px 0 20px 0;
    li {
      padding: 10px;
      height: 400px;
      border-radius: 3px;
      background-clip: content-box;
      background-size: 100% auto;
      background-repeat: no-repeat;
      background-position: center;
      border-style: solid;
      margin: 5px;
      &.small {
        flex-basis: 40%;
      }
      &.large {
        flex-basis: 55%;
      }
    }
  }
}

@media (max-width: 1000px) {
  .our-work .grid li.small,
  .our-work .grid li.large {
    flex-basis: 100%;
  }
}

@media (max-width: 600px) {
  .our-work {
    .grid {
      padding: 30px 0;
      li.small,
      li.large {
        padding: 10px 0;
      }
    }
  }
}
</style>
