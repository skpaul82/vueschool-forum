<template>
  <div class="col-large push-top">
    <h1>{{ thread.title }}</h1>

    <PostList :posts="threadPosts"/>

    <div class="">
      <form @submit.prevent="addPost">
        <div class="form-group row">
          <label for="newPost" class="col-sm-1-12 col-form-label"></label>
          <div class="col-sm-1-12">
            <textarea v-model="newPost" class="form-control" name="newPost" id="newPost" placeholder="Write here.."></textarea>
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
  </div>
</template>

<script>
import PostList from '@/components/PostList'
import sourceData from '@/data.json'
export default {
  name: 'ThreadShow',
  components: {
    PostList
  },
  props: {
    id: {
      required: true,
      type: String
    }
  },
  data () {
    return {
      threads: sourceData.threads,
      posts: sourceData.posts,
      newPost: null
    }
  },
  computed: {
    thread () {
      return this.threads.find(thread => thread.id === this.id)
    },
    threadPosts () {
      return this.posts.filter(post => post.threadId === this.id)
    }
  },
  methods: {
    addPost () {
      const postId = 'aaa' + Math.random()
      const post = {
        id: postId,
        text: this.newPost,
        publishdAt: Math.floor(Date.now() / 1000),
        threadId: this.id,
        userId: '7uVPJS9GHoftN58Z2MXCYDqmNAh2'
      }
      this.posts.push(post)
      this.thread.posts.push(postId)
      this.newPost = null
    }
  }
}
</script>

<style scoped>
</style>
