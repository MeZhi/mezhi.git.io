<template>
    <div id="single-blog">
        <h1>{{blog.title}}</h1>
        <article>{{blog.content}}</article>
        <p>作者：{{blog.author}}</p>
        <p>分类：</p>
        <ul>
            <li v-for="category in blog.categories">
                {{category}}
            </li>
        </ul>
        <router-link :to="'/edit/' + id">编辑</router-link>
        <button @click="deleteSingleBlog()">删除</button>
    </div>

</template>

<script>
import axios from 'axios'
export default {
    name:"single-blog",
    data(){
        return{
            id:this.$route.params.id,
            blog:{}
        }
    },
    created(){
        // this.$http.get('https://my-blog-d048a.firebaseio.com/posts/'+ this.id+".json")
        axios.get('https://my-blog-d048a.firebaseio.com/posts/'+ this.id+".json")
        .then((data) => {
            // this.blog = data.body;
            // console.log(data);
            return this.blog = data.data;
        })
    },
    methods:{
        deleteSingleBlog(){
            this.$http.delete('https://my-blog-d048a.firebaseio.com/posts/'+ this.id+".json")
            .then(response => {
                this.$router.push({path:'/'})
            })
        }
    }
}
</script>

<style scoped>
    #single-blog{
        max-width:1280px;
        margin: 0 auto;
        padding: 20px;
        background: #eee;
        border: 1px dotted #aaa;
    }
    button,a{
        display: inline-block;
        width: 60px;
        font-size: 18px;
        color: #fff;
        text-align: center;
        background:crimson;
        border-radius: 5px;
    }
    a{
        height: 27px;
        text-decoration: none;
        box-shadow:2px 2px 1px rgb(121, 120, 120);
    }
</style>