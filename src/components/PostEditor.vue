<template>
    <div class="">
      <form @submit.prevent="save">
        <div class="form-group row">
          <label for="newPost" class="col-sm-1-12 col-form-label"></label>
          <div class="col-sm-1-12">
            <textarea v-model="text" class="form-control" placeholder="Write here.."></textarea>
          </div>
        </div>
        <div class="form-group row">
          <div class="offset-sm-2 col-sm-10">
            <button type="submit" class="btn btn-primary">
              Submit
            </button>
          </div>
        </div>
      </form>
    </div>
</template>

<script>
export default {
  name: 'EditorPost',
  data () {
    return {
      text: null
    }
  },
  methods: {
    save () {
      const postId = 'aaa' + Math.random()
      const post = {
        id: postId,
        text: this.text,
        publishdAt: Math.floor(Date.now() / 1000),
        userId: '7uVPJS9GHoftN58Z2MXCYDqmNAh2'
      }
      this.$emit('save', { post })
      this.text = null
    }
  }
}
</script>

<style scoped>

</style>
