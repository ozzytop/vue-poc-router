<template>
    <h1>Jobs</h1>
    <div v-if="jobs.length">
        <div v-for="job in jobs" :key="job.id" class="job">
        
            <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
                <h3>{{job.title}}</h3>    
            </router-link>
        </div>
    </div>
    <div v-else>Loading Jobs</div>

</template>

<script>
export default {
    data() {
        return {
            jobs: []
 /*           {id: 1, title: "UX/UI", details: "Lorem ipsum"},
            {id: 2, title: "FrontEnd", details: "Lorem ipsum"},
            {id: 3, title: "Backend", details: "Lorem ipsum"}*/
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs')
            .then((res) => {
                return res.json();
            })
            .then((data) => {
                this.jobs = data;
            })
            .catch(err => console.log(err.message))
    }
}
</script>

<style>
.job h3{
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600;
    cursor: pointer;
    color: #444;
}
.job h3:hover{
    background: #ddd;
}
.job a{
    text-decoration: none;
}
</style>