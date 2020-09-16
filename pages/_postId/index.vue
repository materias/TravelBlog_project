<template>
    <div id="post">
        <h1>{{ title }}</h1>
        <div class="post-thumbnail" :style="{backgroundImage: 'url(' + image + ')'}"></div>
        <p>{{ content }}</p>
    </div>
</template>

<script>
export default {
    asyncData(context) {
        return context.app.$storyapi.get('cdn/stories/blog/' + context.params.postId, {
            version: 'draft'
        }).then(response => {
            return { 
                image: response.data.story.content.thumbnail,
                title: response.data.story.content.title,
                content: response.data.story.content.content
            }
        })

    }
}
</script>

<style scoped>
#post {
    margin-top: 100px;
    margin-left: 40px;
    margin-right: 40px;
    text-align: justify;
    font-size: 1.5rem;
}

.post-thumbnail {
    width: 100%;
    height: 300px;
    background-size: cover;
    background-position: center;
    margin: 0 auto;
    margin-top: 30px;
}

h1 {
    text-align: center;
    font-size: 3rem;
    width: 700px;
    margin: 0 auto;
}
</style>