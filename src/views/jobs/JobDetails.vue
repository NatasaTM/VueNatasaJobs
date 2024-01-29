<template>
    <div v-if="job">
        <h1>{{ job.title}}</h1>
    <p>The job ID is {{ id }}</p>
    <p> {{ job.details }}</p>
    </div>
    <div v-else>
        <p>Loading job details...</p>
    </div>
    
</template>

<script>
    export default {
        props: ['id'],
        data(){
          return {
            job: null
          }
        },
        mounted(){
            console.log('ID:', this.id); // Log the ID prop
        fetch('http://localhost:3000/jobs/' + this.id)
            .then((res) => res.json())
            .then(data => {
                console.log('Data:', data); // Log the data returned by the fetch request
                this.job = data;
            })
            .catch(err => console.log(err.message));
    }
}
</script>

<style>

</style>