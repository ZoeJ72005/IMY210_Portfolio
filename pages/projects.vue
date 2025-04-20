<template>
    <div class="projects">
      <h1>My Projects</h1>
      <div class="project-list">
        <ProjectCard
          v-for="(project, index) in projects"
          :key="index"
          :project="project"
        />
      </div>
    </div>
  </template>
  
  <script setup>
  import ProjectCard from '~/components/ProjectCard.vue'
  const projects = ref([])
  
  onMounted(async () => {
    const res = await fetch('https://api.github.com/users/ZoeJ72005/repos')
    const data = await res.json()
    const selected = ['IMY210PA2', 'zoeStudyGroup', 'Practical5']
    projects.value = data
      .filter(repo => selected.includes(repo.name))
      .map(repo => ({
        title: repo.name,
        description: repo.description || 'No description provided',
        link: repo.html_url
      }))
  })
  </script>
  
  <style scoped>
  .projects {
    padding: 2rem;
    text-align: center;
  }
  
  .project-list {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    margin-top: 2rem;
  }
  </style>
  