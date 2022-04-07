<template>
    <div>
        <h3>Customer reviews</h3>
        
        <div v-if="!$fetchState.pending">
            <ReviewCard 
            v-for="reviewer in reviewers.results"
            :key="reviewer.login.uuid"
            :review="reviewer"
            />
        </div>
        <div v-else><Loading class=""></Loading></div>
    </div>
</template>

<script>
   export default {
    data() {
      return {
        reviewrs: []
      }
    },
    async fetch () {
      this.reviewers = await fetch(
        'https://randomuser.me/api/?results=5'
      ).then(res => res.json())
    }
  }
</script>

<style lang="scss" scoped>

</style>
