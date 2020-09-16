<template>
  <section id="posts">
    <PostPreview 
    v-for="post in posts"
    :key="post.id"
    :title="post.title"
    :excerpt="post.previewText"
    :thumbnailImage="post.thumbnailUrl"
    :id="post.id"
    :date="post.date"
    />
  </section>
</template>

<script>
import PostPreview from '../components/Blog/PostPreview'
export default {
  components: {
    PostPreview
  },
  asyncData(context) {
    return context.app.$storyapi
      .get('cdn/stories', {
        version: 'draft',
        starts_with: 'blog/'
    }).then(response => {
      console.log(response);
      return {
        posts: response.data.stories.map(blogpost => {
          return {
            id: blogpost.slug,
            title: blogpost.content.title,
            previewText: blogpost.content.summary,
            thumbnailUrl: blogpost.content.thumbnail,
            date: blogpost.content.date
          }
        })
      }
    })
  },
  // data() {
  //   return {
  //     posts: [
  //       {
  //         title: 'Amazing Tanzania',
  //         previewText: 'This preview',
  //         thumbnailUrl: 'https://www.national-geographic.pl/media/cache/slider_big/uploads/media/default/0001/92/d1566dbc94dbec67672cc0a7827bc2a75e0cb4c6.jpeg',
  //         id: 'amazing-tanzania'
  //       },
  //       {
  //         title: 'Stunning Cocos Islands',
  //         previewText: 'Next preview',
  //         thumbnailUrl: 'https://img.theculturetrip.com/1024x574/smart/wp-content/uploads/2018/07/shutterstock_352103564.jpg',
  //         id: 'stunning-cocos-islands'
  //       }
  //     ]
  //   }
  // }
}
</script>

<style scoped>
#posts {
  padding-top: 2rem;
  padding-left: 1rem;
  padding-right: 1rem;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

@media (min-width: 35rem) {
  #posts {
    flex-direction: row;
  }
}
</style>
