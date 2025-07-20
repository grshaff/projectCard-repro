<template>
    <div class="flex flex-wrap ms-5" >
        <projectCard
            v-for="(project, index) in projects"
            :key="index"
            :projectName="project.name"
            :projectDesc="project.desc"
            :projectStatus="project.status"
        />
    </div>
  </template>

<script setup>
    import projectCard from '../components/projectCard.vue'

    const projectS = {
        enjoyreads: {
            name: "enjoyreads",
            logo: "../",
            desc: "A web application to read PDFs and ePUBs as books",
            status: false,
            URL: "#/",
        },
        revmycv: {
            name: "reviewmycv",
            logo: "../",
            desc: "Quick CV reviewer built with AI to analyze and fix your resume.",
            status: false,
            URL: "#/",
        },
        shiftGen: {
            name: "Shift Generator",
            logo: "../",
            desc: "Tool for generating shift schedules, creates excel as output",
            status: true,
            URL: "#/",
        },
        btps: {
            name: "Bandung TPS Monitor",
            logo: "../",
            desc: "Web to monitor trash capacity in Bandung, connects with IoT developement",
            status: true,
            URL: "#/",
        }
    }

    const projects = Object.values(projectS)
</script>