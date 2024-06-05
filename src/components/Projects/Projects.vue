<script setup lang="ts">
import ProjectsItem from '@/components/Projects/ProjectsItem.vue';
import { useLanguageSwitcher } from '@/composables/useLanguageSwitcher';
import { TechnologyType } from '@/types/TechnologyType';
import { FadeDown, FadeLeft, FadeRight } from '@/constants/app';

const { t } = useLanguageSwitcher();

type ProjectType = {
    titleKey: string,
    contentKey: string,
    github: string,
    online?: string,
    technologies: TechnologyType[]
};
const projects: ProjectType[] = [
    {
        titleKey: 'projects.projectsItems.WDI.title',
        contentKey: 'projects.projectsItems.WDI.content',
        github: 'https://github.com/dhanush-rahul/-Data-analysis-on-World-Development-Indicators',
        technologies: [
            'python', 'r'
        ]
    },
    {
        titleKey: 'projects.projectsItems.FDI.title',
        contentKey: 'projects.projectsItems.FDI.content',
        github: 'https://github.com/dhanush-rahul/Food-Drug-Interaction-Using-ML-algorithms',
        technologies: [
            'python'
        ]
    },
    {
        titleKey: 'projects.projectsItems.toxicity.title',
        contentKey: 'projects.projectsItems.toxicity.content',
        github: 'https://github.com/dhanush-rahul/Toxicity-Prediction-Challenge-',
        technologies: [
            'python'
        ]
    },
    {
        titleKey: 'projects.projectsItem.itTicketing.title',
        contentKey: 'projects.projectsItem.itTicketing.content',
        github: 'https://github.com/dhanush-rahul/IT-Ticketing-Platform/tree/main/IT-Ticketing-Platform-main',
        technologies:['python', 'angular']
    },
    {
        titleKey: 'projects.projectsItem.rental.title',
        contentKey: 'projects.projectsItem.rental.content',
        github: 'https://github.com/shivapriyasunnam/house-rental-app',
        technologies: ['kotlin']
    },
    {
        titleKey: 'projects.projectsItems.portfolio.title',
        contentKey: 'projects.projectsItems.portfolio.content',
        github: 'https://github.com/dhanush-rahul',
        technologies: ['typescript', 'vue', 'less', 'pwa']
    }
];

</script>

<template>
    <section
        id="projects"
        class="projects"
    >
        <h2 :data-aos="FadeDown" class="title">{{ t('projects.title') }}</h2>

        <div class="items">
            <ProjectsItem
                v-for="(project, index) in projects"
                :key="index"
                :title="t(project.titleKey)"
                :content="t(project.contentKey)"
                :technologies="project.technologies"
                :github="project.github"
                :online="project.online"
                :animation="index % 2 === 0 ? FadeRight : FadeLeft"
            />
        </div>
    </section>
</template>

<style lang="less" scoped>
@import '@/styles/variables.less';

.projects {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 65%;
    min-height: 50vh;
    margin: 0 auto;
    padding-bottom: 1rem;

    .title {
        float: left;
        width: 100%;
        min-height: 3rem;
        text-align: center;
        font-family: 'LatoFontBold', serif;
        font-size: 3rem;
        color: @blue-color;
    }
    .items {
        float: left;
        width: 100%;
        padding: 0.5rem;
    }
}

@media (min-width: @first-breakpoint) {
    .projects {
        // min-width: 40rem;
        // max-width: 42rem;
        padding-bottom: 7rem;

        .title {
            min-height: 4rem;
        }
    }
}

</style>
