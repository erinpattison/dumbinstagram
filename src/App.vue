<template>
  <Header title="Dumb Instagram" />
  <main>
    <Post
      v-for="(post, index) in posts"
      :key="post.profileName"
      :saved="post.saved"
      :liked="post.liked"
      :likeCount="post.likeCount"
      @postLiked="postLiked(index)"
      @savedPost="savedPost(index)"
      :textSize="post.textSize"
    >
      <template #avatar>
        <img class="avatar" :src="post.avatar" />
      </template>
      <template #profile-name>{{ post.profileName }}</template>
      <template #post-pic>
        <img class="post-pic" :src="post.profilePic" />
      </template>
    </Post>
  </main>
</template>

<script>
import Post from "./components/Post.vue";
import Header from "./components/Header.vue";
export default {
  name: "App",
  components: {
    Header: Header,
    Post: Post,
  },
  data: function () {
    return {
      posts: [
        {
          likeCount: Math.floor(Math.random() * 999),
          saved: false,
          liked: false,
          profileName: "larryipsum",
          avatar: "https://assets.codepen.io/5737230/10.jpg",
          profilePic: "https://assets.codepen.io/5737230/post-1.jpg",
          textSize: "medium",
        },
        {
          likeCount: Math.floor(Math.random() * 999),
          saved: false,
          liked: false,
          profileName: "taperfootman",
          avatar: "https://assets.codepen.io/5737230/7.jpg",
          profilePic: "https://assets.codepen.io/5737230/post-5.jpg",
          textSize: "medium",
        },
        {
          likeCount: Math.floor(Math.random() * 999),
          saved: false,
          liked: false,
          profileName: "clipclopjunkie",
          avatar: "https://assets.codepen.io/5737230/8.jpg",
          profilePic: "https://assets.codepen.io/5737230/post-6.jpg",
          textSize: "medium",
        },
        {
          likeCount: Math.floor(Math.random() * 999),
          saved: false,
          liked: false,
          profileName: "highhighlands",
          avatar: "https://assets.codepen.io/5737230/9.jpg",
          profilePic: "https://assets.codepen.io/5737230/post-7.jpg",
          textSize: "medium",
        },
        {
          likeCount: Math.floor(Math.random() * 999),
          saved: false,
          liked: false,
          profileName: "lifejacketchestplate",
          avatar: "https://assets.codepen.io/5737230/1_1.png",
          profilePic: "https://assets.codepen.io/5737230/post-8.jpg",
          textSize: "medium",
        },
        {
          likeCount: Math.floor(Math.random() * 999),
          saved: false,
          liked: false,
          profileName: "glamoursalad",
          avatar: "https://assets.codepen.io/5737230/2_1.png",
          profilePic: "https://assets.codepen.io/5737230/post-9.jpg",
          textSize: "medium",
        },
        {
          likeCount: Math.floor(Math.random() * 999),
          saved: false,
          liked: false,
          profileName: "althoughbeetroot",
          avatar: "https://assets.codepen.io/5737230/3.jpg",
          profilePic: "https://assets.codepen.io/5737230/post-2.jpg",
          textSize: "medium",
        },
      ],
    };
  },
  methods: {
    postLiked: function (index) {
      // alert(index);
      this.posts[index].liked = !this.posts[index].liked;
    },
    savedPost: function (index) {
      this.posts[index].saved = !this.posts[index].saved;
    },
  },
};
</script>

<style>
main {
  margin-top: 100px;
}
.post-pic {
  width: 40vw;
  min-width: 100%;
  max-width: 100%;
}
.avatar {
  max-width: 42px;
  border-radius: 50%;
  margin: 0 10px 0 0;
}
@media only screen and (max-width: 700px) {
  main {
    margin-top: 5rem;
  }
}
</style>
