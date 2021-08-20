<template>
  <div class="blog-page">
    <div v-for="blog in blogs" :key="blog.id">
      <div>Title: {{ blog.title }}</div>
      <div>Desc: {{ blog.description }}</div>
    </div>
    <div v-if="blogs.length === 0">No blogs {{ titledesc }}</div>
    <br/>
    <input v-model="newBlog.title"/>
    <input v-model="newBlog.description"/>
    <button @click="submitblog">Submit</button>
    <button @click="blogs = []">Clear</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newBlog: {
        title: '',
        description: ''
      },
      blogs: [
        {
          id: 1,
          title: 'Title A',
          description: 'Desc A'
        },
        {
          id: 2,
          title: 'Title B',
          description: 'Desc B'
        },
        {
          id: 3,
          title: 'Title C',
          description: 'Desc C'
        }
      ]
    }
  },
  methods: {
    submitblog () {
      this.blogs.push({
        id: this.blogs.length,
        title: this.newBlog.title,
        description: this.newBlog.description
      })
      this.newBlog.title = ''
      this.newBlog.description = ''
    }
  },
  computed: {
    titledesc () {
      return this.newBlog.title + ' ' + this.newBlog.description
    }
  }
}
</script>
