<template>
<div style="display: flex; width: 100%">
      <figure class="media-left">
        <img class="image is-64x64"
          v-bind:src="submission.submissionImage">
      </figure>
      <div class="media-content">
        <div class="content">
          <p>
            <strong>
              <a v-bind:href="submission.url" class="has-text-info">
                {{ submission.title }}
              </a>
              <span class="tag is-small">#{{ submission.id }}</span>
            </strong>
            <br>
              {{ submission.description }}
            <br>
            <small class="is-size-7">
              Submitted by:
              <img class="image is-24x24"
                v-bind:src="submission.avatar">
            </small>
          </p>
        </div>
      </div>
      <div class="media-right">
        <span class="icon is-small" v-on:click="upvote(submission.id)">
          <i class="fa fa-chevron-up"></i>
            </span>
          <span class="icon is-small" v-on:click="devote(submission.id)">
           <i class="fa fa-chevron-down"></i> 
          </span>
          <strong class="has-text-info">{{ submission.votes }}</strong>
      </div>
    </div>
</template>

<script>
export default {
  name: 'submissionComponent',
  props: ['submission', 'submissions'],
    methods: {
      upvote: function(id) {
        const submission = this.submissions.find(function(submission) {
          return submission.id === id;
        });
         submission.votes++;
      },
      devote: function(id) {
        let submission = this.submissions.find(function(submission) {
          return submission.id === id;
        });
        submission.votes--;
        alert("devoted");      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
