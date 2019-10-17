<template>
<div id="posts">
    <PostPreview
    v-for="post in posts"
    :key="post.id"
    :title="post.title"
    :excerpt="post.previewText"
    :thumbnailImage="post.thumbnailUrl"
    :id="post.id"/>
</div>
</template>

<script>
import PostPreview from "@/components/Blog/PostPreview";

export default {
  components: {
    PostPreview
  },

  asyncData(context) {
    return context.app.$storyapi
      .get("cdn/stories", {
        version: "draft",
        starts_with: "blog/"
      })
      .then(res => {
        return {
          posts: res.data.stories.map(bp => {
            return {
              id: bp.slug,
              title: bp.content.title,
              previewText: bp.content.summary,
              thumbnailUrl: bp.content.thumbnail
            };
          })
        };
      });
  }
  // data() {
  //   return {
  //     posts: [
  //       {
  //         title: "A new bigining ",
  //         previewText: "This will be awesome",
  //         thumbnailUrl:
  //           "https://pinchofyum.com/wp-content/uploads/DeLallo-Pizza-1.jpg",
  //         id: "a-new-beginig "
  //       },
  //       {
  //         title: "A second bigining ",
  //         previewText: "This will be also awesome",
  //         thumbnailUrl:
  //           "https://media-manager.starsinsider.com/1920/na_5ad61109471ea.jpg",
  //         id: "a-second-beginig "
  //       }
  //     ]
  //   };
  // }
};
</script>

<style scoped>
#posts {
  padding-top: 2rem;
  display: flex;
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
