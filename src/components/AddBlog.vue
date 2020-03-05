<template>
  <div class="add-blog">
      <h2>添加博客</h2>
      <form v-if="!subminted">
        <label>博客标题</label>
        <input type="text" v-model="blog.title" />

        <br>
        
        <label>博客内容</label>
        <textarea v-model="blog.content"></textarea>

        <div id="checkboxes">
          <label>Vue.js</label>
          <input type="checkbox" value="Vue.js" v-model="blog.categories">
          <label>Node.js</label>
          <input type="checkbox" value="Node.js" v-model="blog.categories">
          <label>Rect.js</label>
          <input type="checkbox" value="Rect.js" v-model="blog.categories">
          <label>Angular.js</label>
          <input type="checkbox" value="Angular.js" v-model="blog.categories">
        </div>
        <label>作者：</label>
        <select v-model="blog.author">
          <option v-for="author in authors">
            {{author}}
          </option>
        </select>
        <button v-on:click.prevent="post">添加博客</button>
      </form>
  
      <div v-if="subminted">
        <h3>你的博客发送成功了！</h3>
      </div>

      <div id="previer">
        <h3>博客总览</h3>
        <p>博客标题:{{blog.title}}</p>
        <p>博客内容:</p>
        <p>{{blog.content}}</p>
        <p>博客分类</p>
        <ul>
          <li v-for="category in blog.categories">
            {{category}}
          </li>
        </ul>
        <p>作者：{{blog.author}}</p>
      </div>
  </div>
</template>

<script>

export default {
  name: 'add-blog',
  data () {
    return {
      blog:{
        title:"",
        content:"",
        categories:[],
        author:""
      },
      authors:["TaylorSwift","Jerry","Tom"],
      subminted:false
    }
  },
  methods:{
    post:function(){
      this.$http.post("http://jsonplaceholder.typicode.com/posts",{
        title:this.blog.title,
        body:this.blog.content,
        userId:1
        })
        .then(function(data){
          console.log(data);
          this.subminted = true;
        });
    }
  }
}
</script>


<style scoped>

</style>
