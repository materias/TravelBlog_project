<template>
    <section id="about-page">
        <h1 class="about-page-title">{{ title }}</h1>
        <div class="about-page-description">
            <div class="photo" :style="{backgroundImage: 'url(' + photo + ')'}"></div>
            <div v-html="$md.render(description)">{{ description }}</div>
        </div>
        <p v-html="$md.render(content)" class="about-page-content">{{ content }}</p>
    </section>
</template>

<script>
export default {
    asyncData(context) {
        return context.app.$storyapi.get('cdn/stories/about', {
            version: 'draft'
        }).then(response => {
            return {
                title: response.data.story.content.title,
                photo: response.data.story.content.photo,
                description: response.data.story.content.description,
                content: response.data.story.content.content
            }
        })
    }
}
</script>

<style scoped>
.about-page-title {
    grid-area: grid-title;
    font-size: 2rem;
}
.about-page-description {
    grid-area: grid-description;
    line-height: 50%;
}
.about-page-content {
    grid-area: grid-content;
    line-height: 200%;
    font-size: 1.3rem;
}

#about-page {
    width: 80%;
    max-width: 1000px;
    display: grid;
    grid-template-columns: 250px auto;
    grid-template-rows: auto;
    grid-template-areas:
        "grid-title grid-title" 
        "grid-description grid-content";
    margin-top: 100px;
    margin-left: 35px;
    font-size: 1.1rem;
    text-align: justify;
}

.photo {
    width: 200px;
    height: 200px;
    border-radius: 100%;
}


</style>