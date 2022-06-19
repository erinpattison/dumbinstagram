<template>
  <!-- I'm getting an error saying that the emit events have to be in kebob case, but 
it doesn't actually seem to be affecting anything- leaving it as is, let me know if 
this is actually a thing- I don't think I was getting this error when we were working on it. -->
  <div class="post" v-on:dblclick="$emit('postLiked')">
    <div class="post-header">
      <slot name="avatar"
        ><img src="https://assets.codepen.io/5737230/2.png"
      /></slot>
      <p>
        <strong>
          <slot name="profile-name">loremipsum</slot>
        </strong>
      </p>
    </div>
    <slot name="post-pic">
      <img
        class="post-pic"
        src="https://assets.codepen.io/5737230/post-7.jpg"
      />
    </slot>
    <div class="user-actions">
      <span class="user-actions__left">
        <button @click="$emit('postLiked')">
          <svg
            v-if="liked == false"
            aria-label="Like"
            class="like"
            color="#262626"
            fill="#262626"
            height="24"
            role="img"
            viewBox="0 0 24 24"
            width="24"
          >
            <path
              d="M16.792 3.904A4.989 4.989 0 0121.5 9.122c0 3.072-2.652 4.959-5.197 7.222-2.512 2.243-3.865 3.469-4.303 3.752-.477-.309-2.143-1.823-4.303-3.752C5.141 14.072 2.5 12.167 2.5 9.122a4.989 4.989 0 014.708-5.218 4.21 4.21 0 013.675 1.941c.84 1.175.98 1.763 1.12 1.763s.278-.588 1.11-1.766a4.17 4.17 0 013.679-1.938m0-2a6.04 6.04 0 00-4.797 2.127 6.052 6.052 0 00-4.787-2.127A6.985 6.985 0 00.5 9.122c0 3.61 2.55 5.827 5.015 7.97.283.246.569.494.853.747l1.027.918a44.998 44.998 0 003.518 3.018 2 2 0 002.174 0 45.263 45.263 0 003.626-3.115l.922-.824c.293-.26.59-.519.885-.774 2.334-2.025 4.98-4.32 4.98-7.94a6.985 6.985 0 00-6.708-7.218z"
            ></path>
          </svg>

          <svg
            v-else
            aria-label="Unlike"
            class="_8-yf5"
            color="#ed4956"
            fill="#ed4956"
            height="24"
            role="img"
            viewBox="0 0 48 48"
            width="24"
          >
            <path
              d="M34.6 3.1c-4.5 0-7.9 1.8-10.6 5.6-2.7-3.7-6.1-5.5-10.6-5.5C6 3.1 0 9.6 0 17.6c0 7.3 5.4 12 10.6 16.5.6.5 1.3 1.1 1.9 1.7l2.3 2c4.4 3.9 6.6 5.9 7.6 6.5.5.3 1.1.5 1.6.5s1.1-.2 1.6-.5c1-.6 2.8-2.2 7.8-6.8l2-1.8c.7-.6 1.3-1.2 2-1.7C42.7 29.6 48 25 48 17.6c0-8-6-14.5-13.4-14.5z"
            ></path>
          </svg>
        </button>

        <button>
          <svg
            aria-label="Comment"
            class="_8-yf5"
            color="#262626"
            fill="#262626"
            height="24"
            viewBox="0 0 24 24"
            width="24"
          >
            <path
              d="M20.656 17.008a9.993 9.993 0 10-3.59 3.615L22 22z"
              fill="none"
              stroke="currentColor"
              stroke-linejoin="round"
              stroke-width="2"
            ></path>
          </svg>
        </button>

        <button>
          <svg
            aria-label="Share Post"
            class="_8-yf5"
            color="#262626"
            fill="#262626"
            height="24"
            role="img"
            viewBox="0 0 24 24"
            width="24"
          >
            <line
              fill="none"
              stroke="currentColor"
              stroke-linejoin="round"
              stroke-width="2"
              x1="22"
              x2="9.218"
              y1="3"
              y2="10.083"
            ></line>
            <polygon
              fill="none"
              points="11.698 20.334 22 3.001 2 3.001 9.218 10.084 11.698 20.334"
              stroke="currentColor"
              stroke-linejoin="round"
              stroke-width="2"
            ></polygon>
          </svg>
        </button>
      </span>

      <span class="user-actions__right">
        <button @click="$emit('savedPost')">
          <svg
            v-if="saved == false"
            color="#262626"
            aria-label="Save"
            class="save"
            height="24"
            role="img"
            viewBox="0 0 24 24"
            width="24"
          >
            <polygon
              fill="none"
              points="20 21 12 13.44 4 21 4 3 20 3 20 21"
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
            ></polygon>
          </svg>

          <svg
            v-else
            aria-label="Remove"
            class="_8-yf5"
            color="#262626"
            fill="#262626"
            height="24"
            role="img"
            viewBox="0 0 24 24"
            width="24"
          >
            <path
              d="M20 22a.999.999 0 01-.687-.273L12 14.815l-7.313 6.912A1 1 0 013 21V3a1 1 0 011-1h16a1 1 0 011 1v18a1 1 0 01-1 1z"
            ></path>
          </svg>
        </button>
      </span>
    </div>
    <span class="like-count">
      <strong>{{ likeCount }} likes</strong>
    </span>
    <div class="caption">
      <p
        :class="{
          large: textSize === 'large',
          small: textSize === 'small',
          medium: textSize === 'medium',
        }"
      >
        <strong><slot name="profile-name"> </slot></strong>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi, nam.
        Magni perferendis, iure aut est harum officiis temporibus praesentium
        voluptates sapiente accusantium, eligendi voluptate quos tempore amet
        labore nobis laudantium?
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    saved: Boolean,
    liked: Boolean,
    likeCount: Number,
    textSize: String,
  },

  methods: {
    // leaving these here for testing purposes
    savePost() {
      alert("Saved");
    },
    likePost() {
      alert("Liked");
    },
  },
};
</script>

<!-- Use preprocessors via the lang attribute! e.g. <style lang="scss"> -->
<style scoped>
* {
  font-family: sans-serif;
}
.post {
  width: 40vw;
  min-height: 40vw;
  border: 1px solid #ccc;
  border-radius: 5px;
  /*   background-color: #dcdcdc; */
  margin: 50px auto;
  overflow: hidden;
}
.post-header {
  background-color: #fff;
  /* border: 1px solid #ccc; */
  font-family: sans-serif;
  display: flex;
  align-items: center;
  padding: 14px;
}
.post-header img {
  max-width: 32px;
  border-radius: 50%;
  margin: 3px 5px;
}
.post-header p {
  margin: 0;
  font-size: 14px;
}
.post-pic {
  width: 40vw;
  min-width: 100%;
  max-width: 100%;
}
.aside {
  width: 40vw;
  border: 1px solid #dcdcdc;
}
.container-a {
  width: 60vw;
  height: 60vw;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin: 50px;
}

.user-actions {
  display: flex;
  padding: 5px;
}
.user-actions span {
  width: 50%;
}

.user-actions__right {
  display: flex;
  justify-content: flex-end;
}

.like-count {
  margin: 0 5px;
  font-size: 12px;
  padding: 5px;
}
.caption {
  padding: 0 10px;
}
button {
  background-color: transparent;
  border: none;
}
.large {
  font-size: 50px;
}
.small {
  font-size: 12px;
}
.medium {
  font-size: 18px;
}
@media only screen and (max-width: 700px) {
  .post {
    width: 100vw;
    margin: 0;
    border-radius: 0;
    border-bottom: 1px solid #ccc;
  }
}
</style>
