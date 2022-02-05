<template>
    <div v-if="job">
        <h1>{{job.title}}</h1>
        <p>The job is {{ id }}</p>
        <p>{{job.details}}</p>        
    </div>
    <div v-else>
        Loading details
    </div>
</template>

<script>
export default {
    // we send the id as a prop. Still we can get it from the this.$route.params.id
    props: [ 'id' ],
    data() {
        return {
            job: null
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs/' + this.id)
            .then(res => res.json() )
            .then(data => this.job = data )
            .catch(err => console.log(err.message))
    }
}
</script>

<style>

</style>