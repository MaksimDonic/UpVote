<template>
  <div id="app">
    <h2 class="title has-text-centered dividing-header">UpVote!</h2>
    <div class="section">
      <article v-for="submission in sortedSubmissions" :key="submission.id"   class="media" :class="{ 'blue-border': submission.votes >= 20 }">
        <submission-component   :submission="submission"  :submissions="sortedSubmissions">
        </submission-component>
      </article>
    </div> 
    
  </div>
</template>

<script>

import submissionComponent from './components/Submission.vue'

export default {
  name: 'app',
  components: {
 'submission-component': submissionComponent 
  }
,
 data: function() {
    return {
     submissions:  [
    {
      id: 1,
      title: 'Yellow Pail',
      description: 'On-demand sand castle construction expertise.',
      url: '#',
      votes: 16,
      avatar: '../images/avatars/daniel.jpg',
      submissionImage: '../images/submissions/image-aqua.png',
    },
    {
      id: 2,
      title: 'Supermajority: The Fantasy Congress League',
      description: 'Earn points when your favorite politicians pass legislation.',
      url: '#',
      votes: 11,
      avatar: '../images/avatars/kristy.png',
      submissionImage: '../images/submissions/image-rose.png',
    },
    {
      id: 3,
      title: 'Tinfoild: Tailored tinfoil hats',
      description: 'We have your measurements and shipping address.',
      url: '#',
      votes: 17,
      avatar: '../images/avatars/veronika.jpg',
      submissionImage: '../images/submissions/image-steel.png',
    },
    {
      id: 4,
      title: 'Haught or Naught',
      description: 'High-minded or absent-minded? You decide.',
      url: '#',
      votes: 9,
      avatar: '../images/avatars/molly.png',
      submissionImage: '../images/submissions/image-aqua.png',
    }
  ]
    }
  },
      computed: {
    sortedSubmissions: function () {
      let submissions = this.submissions;
      return submissions.sort(function(a,b) {
        return b.votes - a.votes;
      });
      }
    }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
