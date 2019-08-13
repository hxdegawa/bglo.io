<template lang="pug">
  main
    // render data of the person
    //- h1 {{ person.fields.name }}
    // render blog posts
    ArticleCard(v-for="post in posts" :key="post.fields.slug")
      img(:src="post.fields.heroImage.fields.file.url")
      h3 {{ post.fields.title }}
      p {{ post.fields.description }}
      span.date {{ $dateFns.distanceInWordsToNow( post.fields.publishDate, {locale: 'ja'}) }}前
      .tags
        span.tag(v-for="item in post.fields.tags" ) {{ item }}
</template>

<script>
import ArticleCard from '~/components/ArticleCard'
import {createClient} from '~/plugins/contentful.js'

const client = createClient()

export default {
  components: {
    ArticleCard
  },
  asyncData ({env}) {
    return Promise.all([
      client.getEntries({
        'sys.id': env.CTF_PERSON_ID
      }),
      client.getEntries({
        'content_type': env.CTF_BLOG_POST_TYPE_ID,
        order: '-sys.createdAt'
      })
    ]).then(([entries, posts]) => {
      console.log(posts);
      return {
        person: entries.items[0],
        posts: posts.items
      }
    }).catch(console.error);
  }
}
</script>
