<template>
    <div class="project-item">
      <h4 class="project-title">{{ title }}</h4>
      <p class="project-content">{{ content }}</p>
      <div class="project-technologies">
        <TechnologyElement 
            v-for="(tech, index) in props.technologiesUsed" 
            :key="index" 
            :element="tech"
            />
      </div>
      <p class="project-role">
        <ul class="order">
            <li class="points" v-for="(sentence, index) in roleSentences" :key="index">{{sentence}}</li>
        </ul>
      </p>
    </div>
  </template>
  
  <script setup lang="ts">
  import { computed } from 'vue';
  import { useI18n } from 'vue-i18n';
import TechnologyElement from '../TechnologyElement.vue';
  
  const props = defineProps<{
    title: string;
    content: string;
    technologiesUsed: string[];
    role: string;
  }>();

  const roleSentences = props.role.split('. ');
  
  const { t } = useI18n();
  
  const translatedContent = computed(() => t(props.content));
  const translatedRole = computed(() => t(props.role));
  </script>
  
  <style scoped>
  .project-item {
    margin-bottom: 1rem;
    padding: 1rem;
    border: 0.5px solid #ccc;
    border-radius: 0.5rem;
    /* background-color: #f9f9f9; */
    transition: background-color 0.3s;
  }
  
  
  
  .project-title {
    font-size: 1.2rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
  
  .project-content {
    margin: 0.5rem 0;
    font-size: 1rem;
  }
  
  .project-technologies {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.5rem;
  }
  
  .project-tech {
    background-color: #e0e0e0;
    border-radius: 0.25rem;
    padding: 0.25rem 0.5rem;
    font-size: 0.9rem;
  }
  
  .project-role {
    /* font-style: italic  */
    margin-top: 0.5rem;
    margin-left: 0.5rem;
    text-align: left;
  }
  .points{
    padding-top:0.5rem;
  }
  </style>