<template>
  <div class="card">
    <button class="close-button" @click="removeCardFromList">
      ×
    </button>
    <div class="body">
      {{ body }}
      <i
        @click="like = !like"
        :class="{ '-is-liked' : like }"
        class="fa fa-heart card-img"
      />
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      like: false,
    }
  },
  props: {
    body: {
      type: String,
      required: true
    },
    listIndex: {
      type: Number,
      required: true
    },
    cardIndex: {
      type: Number,
      required: true
    }
  },
  methods: {
    removeCardFromList: function() {
      if(confirm('本当にこのカードを削除しますか？')) {
        this.$store.dispatch('removeCardFromList', { cardIndex: this.cardIndex, listIndex: this.listIndex })
      }
    }
  },
}
</script>

<style scoped>
.card {
  position: relative;
}

.card-img {
  position: absolute;
  right: 28px;
  bottom: 8px;
  transition: 0.2s;
}

.card-img.-is-liked {
  color: red;
}
</style>
