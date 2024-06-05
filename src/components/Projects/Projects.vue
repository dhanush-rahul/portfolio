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
        titleKey: 'IT Ticketing Platform',
        contentKey: 'A specialized web application tailored for IT companies, designed to streamline the process of issue reporting and resolution. Spearheaded both front-end and back-end development for a web-based IT ticketing system. Utilized Angular.js to create an intuitive and user-friendly interface, and employed responsive design to ensure compatibility across various devices. Developed secure, efficient back-end APIs using JavaScript and Node.js with PostgreSQL for robust data management. Enhanced database performance and integrity through optimized schema design. Conducted extensive testing to guarantee high functionality and reliability under diverse scenarios. Actively engaged in the Agile process, collaborating with team members to refine the application continually based on feedback and technical insights.',
        github: 'https://github.com/dhanush-rahul/IT-Ticketing-Platform/tree/main/IT-Ticketing-Platform-main',
        technologies:['python', 'angular']
    },
    {
        titleKey: 'Nish Rents - A House Rental App',
        contentKey: 'Engineered an innovative Android house rental application for Antigonish, simplifying accommodation searches with real-time updates and detailed descriptions. Leveraging a modern tech stack including Kotlin and Android Jetpack Compose, the app offers a user-friendly interface and robust security measures, ensuring a seamless experience for renters and property owners. Integrated advanced features like Material Design components and Lottie animations, setting a new standard for rental platforms in the region and providing a comprehensive solution for individuals and families relocating to Antigonish.',
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
