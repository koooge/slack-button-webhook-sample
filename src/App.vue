<template>
  <div id="app">
  <a href="https://slack.com/oauth/v2/authorize?client_id=216559041989.1262107973383&scope=incoming-webhook&user_scope=">
    <img
      alt="Add to Slack"
      height="40"
      width="139"
      src="https://platform.slack-edge.com/img/add_to_slack.png"
      srcSet="https://platform.slack-edge.com/img/add_to_slack.png 1x, https://platform.slack-edge.com/img/add_to_slack@2x.png 2x" />
  </a>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  mounted() {
    const q = this.$route.query
    if (q.code != null) {
      axios.post('https://slack.com/api/oauth.v2.access', {code: q.code})
        .then(res => {
          console.log(res.data)
        })
        .catch(e => console.error(e))
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
