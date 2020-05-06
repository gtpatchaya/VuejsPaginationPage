<template>
  <div>
       <b-col >
       <b-card
        :title="name"
        img-src="https://picsum.photos/600/300/?image=25"
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
        footer="Card Footer"
       >
        <b-card-text>
          Hello this is my bard text
        </b-card-text>
         <b-button href="#" variant="primary">Go somewhere</b-button>
      </b-card>
    </b-col>
  </div>
</template>

<script>
export default {
    props : ["name"]
}
</script>


