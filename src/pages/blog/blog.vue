<template>
  <div class="blog">
    <header>
      <div class="head-top">
        <router-link to="/" tag="div"><img src="./images/home.svg" width="50" height="50"></router-link>
        <h1>zerotop.top</h1>
      </div>
      <div class="head-nav">
        <div>博客</div>
        <div>设计</div>
        <div>时间轴</div>
        <div>留言</div>
      </div>
    </header>
    <div class="blog-main margin">
      <aside class="blog-sort">
        <div><img src="./images/emoji-1.svg"/><span>全部博客</span></div>
        <div><img src="./images/emoji-12.svg"/><span>node</span></div>
        <div><img src="./images/emoji-28.svg"/><span>phython</span></div>
        <div><img src="./images/emoji-1.svg"/><span>sass</span></div>
        <div><img src="./images/emoji-12.svg"/><span>mongoDB</span></div>
        <div><img src="./images/emoji-28.svg"/><span>vue</span></div>
      </aside>
      <article class="blog-article">
        <section class="blog-con margin" v-for="(items,index) in blogs" :key="index">
          <div class="content margin">
            <img :src=items.blogImg>
            <div class="content-desc">
              <h3 class="ellipsis">{{items.description}}</h3>
              <div>
                <h5>2018/5/2</h5>
                <button @click="readMore"><b>Read More >></b></button>
              </div>
            </div>
          </div>
        </section>
      </article>
      <aside class="blog-other">
        <div class="other">
          <div class="music" @click="playMusic">
            <audio
              src="http://m10.music.126.net/20180504103427/0c00e664c9eaa356a8fc86f18ec43a6a/ymusic/7615/9217/8620/bf610c9f7e95efcad2b5ccde600339bf.mp3"
              ref="mp3Btn"></audio>
          </div>
          <div class="book"></div>
          <div class="date"></div>
          <div @click="toTop" class="top" :class="{animate:animate}"></div>
        </div>
      </aside>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
/* eslint-disable */
  export default{
    data () {
      return {
        animate: false,
        blogs: [
          {
            blogImg: 'https://images.unsplash.com/photo-1522205940279-d75807ebcd91?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=6e84041cbb7404fb7fafc42bec0f4a91&auto=format&fit=crop&w=500&q=60',
            description: '欢迎来到zerotop'
          },
          {
            blogImg: 'https://images.unsplash.com/photo-1507550442364-c0a42bd688e0?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=92c60a48a7b047b3a2b603cf6227ad2d&auto=format&fit=crop&w=500&q=60',
            description: '欢迎来到zerotop欢迎来到zerotop欢迎来到zerotop欢迎来到zerotop欢迎来到zerotop欢迎来到zerotop'
          },
          {
            blogImg: 'https://images.unsplash.com/photo-1522205445560-4630427027e3?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=1d6dff78cad1ece4d14fbf6d50ac3325&auto=format&fit=crop&w=500&q=60',
            description: '欢迎来到zerotop'
          }
        ]

      }
    },
    methods: {
      toTop(){
        this.animate = true
        setTimeout(() => {
          document.body.scrollTop = document.documentElement.scrollTop = 0;
          this.animate = false
        }, 1000)
      },
      playMusic(){
        let audio = this.$refs.mp3Btn
        if (audio.paused) {
          audio.play()
        } else {
          audio.pause()
        }

      },
      readMore(){

      }
    }
  }
</script>

<style scoped lang="scss">
  @import "../../style/mixin";

  @keyframes bounce {
    0% {
      width: 50%;
    }
    50% {
      width: 55%;
    }
    100% {
      width: 50%;
    }
  }

  @keyframes toTop {
    0% {
      margin-bottom: 2rem;
    }
    50% {
      margin-bottom: 4rem;
      @include bis('./images/air.svg');
    }
    100% {
      margin-bottom: 2rem;
    }
  }

  @media only screen and (max-width: 420px) {
    #app {
      width: 100%;
      height: 100%;
      .blog-con {
        @include wh(85%, 27rem);
      }
    }
  }

  .blog {
    width: 100%;
    height: 100%;
    header {
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      width: 100%;
      height: 15rem;
      border-radius: 50%;
      margin-top: -7.5rem;
      background-color: #ccc;
      padding-bottom: 2.5rem;
      text-align: center;
      .head-top {
        @include cl;
        display: flex;
        flex-direction: row;
        h1 {
          margin-left: 2rem;
        }
      }
      .head-nav {
        margin-top: 1.5rem;
        width: 20rem;
        @include cl;
        display: flex;
        justify-content: space-around;
      }
    }
    .blog-main {
      margin-top: 2rem;
      width: 90%;
      display: flex;
      justify-content: space-between;
      .blog-sort {
        flex-grow: 1;
        div {
          @include wh(100%, 3rem);
          position: relative;
          vertical-align: bottom;
          margin-bottom: 1.8rem;
          img {
            @include wh(2.2rem, 2.2rem);
            @include ct;
          }
          span {
            width: 50%;
            padding: 7px;
            display: inline-block;
            background-color: #ccc;
            text-align: center;
            border-radius: 5px;
            @include ct;
            left: 3rem;
            &:hover {
              color: #fff;
              background-color: #999;
              animation: bounce 1s ease-in-out infinite;
            }
          }
        }
      }
      .blog-article {
        display: flex;
        flex-direction: column;
        flex-grow: 1;
        .blog-con {
          display: block;
          @include wh(85%, 26.5rem);
          border: 1px solid #ccc;
          border-radius: 5px;
          margin-bottom: 2rem;
          box-shadow: 3px 3px 3px #ddd;
          .content {
            padding: 2rem;
            @include wh(100%, 22rem);
            img {
              @include wh(100%, 100%);
            }
            .content-desc {
              margin-top: 1rem;
              line-height: 2rem;
              h3 {
                width: 30rem;
              }
              div {
                display: flex;
                justify-content: space-between;
                h5 {
                  color: #666666;
                }
                button {
                  border: 2px solid #666;
                  background-color: #fff;
                  padding: 5px 8px 5px 8px;
                  &:hover{
                    background-color: #888;
                    color: #fff;
                  }
                }
              }
            }
          }
        }
      }
      .blog-other {
        position: relative;
        flex-grow: 1;
        text-align: center;
        .other {
          @include cl;
          bottom: 3rem;
          div {
            margin-top: 3rem;
            cursor: pointer;
          }
          @each $bg in music, date, top, book {
            .#{$bg} {
              @include wh(3rem, 3rem);
              @include bis('./images/#{$bg}.svg');
            }
          }
        }
        .animate {
          animation: toTop 2s ease-in-out infinite;
        }
      }

    }

  }
</style>
