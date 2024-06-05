<script setup lang="ts">
import ExperienceItem from '@/components/Experience/ExperienceItem.vue';
import { useLanguageSwitcher } from '@/composables/useLanguageSwitcher';
import { TechnologyType } from '@/types/TechnologyType';
import { FadeDown, FadeLeft, FadeRight } from '@/constants/app';

const { t } = useLanguageSwitcher();

interface CompanyProject{
    title: string,
    contentKey: string,
    technologiesUsed: TechnologyType[],
    role: string
}
type Experience = {
    title: string,
    contentKey: string,
    professionKey: string,
    periodKey: string,
    lengthKey?: string,
    url: string,
    technologies: TechnologyType[],
    companyProjects: CompanyProject[]
};
const experienceItems: Experience = 
    {
        title: 'Associate Software Developer @ coMakeIT Software (Now Xebia)',
        contentKey: 'experience.experienceItems.associate.content',
        professionKey: 'experience.experienceItems.associate.profession',
        periodKey: 'experience.experienceItems.associate.period',
        lengthKey: 'experience.experienceItems.associate.length',
        url: 'https://website.xebia.com/digital-transformation/software-technology/product-engineering/',
        technologies: [
            'microservices', 'git','react', 'spring', 'angular', 'next', 
            'reactnative', 'java', 'javascript', 'jquery','postgresql', 
            'node', 'express', 'bootstrap', 'html','css', 'mysql'
        ],
        companyProjects:[
            {
                title: 'Edmin Software - Book My Assessment',
                contentKey: 'A web application tailored specifically for managing the needs of students with disabilities. The platform facilitates an efficient, user-friendly environment where students can securely log in, upload necessary disability documentation, and subsequently schedule assessments with qualified assessors. This streamlined process ensures that students are appropriately accommodated in their educational environments, thereby enhancing accessibility and compliance with educational standards and regulations. ',
                technologiesUsed: ['react', 'redux', 'ruby', 'graphql', 'docker', 'ci_cd', 'postman', 'github', 'jira', "agile"],
                role: 'Implemented 20+ React components, creating a modular, scalable front end, and utilized React Hooks and Context for managing local and global states, ensuring smooth data flows and reactivity.Developed robust RESTful APIs using Ruby on Rails, enhancing backend efficiency by 30%. Conducted comprehensive API testing using Postman, verifying functionality, reliability, and security with a 99% success rate.Actively participated in all phases of the Agile development process, and used Jira to track and manage project issues, resulting in a 40% improvement in issue resolution time.'
            },
            {
                title: 'Edmin Software - Student Support Portal',
                contentKey: 'A web application meticulously designed to facilitate access to resources for students with disabilities. The platform enables students and parents to sign up and subscribe to essential resources, streamlining the process of resource allocation tailored to individual needs. This application enhances the accessibility of services, ensuring compliance with educational regulations and standards.',
                technologiesUsed: ['angular', 'node', 'javascript', 'postgresql', 'bitbucket', 'jira','agile'],
                role: 'Engineered interactive user interfaces using Angular.js, developed RESTful APIs with JavaScript and Node.js, enhancing backend data management and front-end interactions by 25%. Implemented comprehensive testing strategies using JUnit, achieving a 98% test coverage rate, and actively participated in the Agile development lifecycle, utilizing Jira to increase task completion rate by 35%.'
            },
            {
                title: 'Yantraka.AI',
                contentKey: 'A cutting-edge web application leveraging advanced machine learning algorithms to forecast trends in cryptocurrency markets. The application provides highly accurate, 30-minute interval predictions, utilizing historical data and real-time analysis to serve financial professionals and enthusiasts with actionable insights.',
                technologiesUsed: ['angular', 'python', 'ml', 'postgresql', 'bitbucket', 'jira', 'agile'],
                role: 'Spearheaded the development of the application using Angular.js, creating a robust and adaptable front-end architecture. Managed the full software development cycle following Agile practices, ensuring timely deliveries.Ensured adherence to project specifications throughout the development process.'
            },
            {
                title: 'Telligent Community',
                contentKey: 'An integrated community platform that supports a range of applications, including forums, blogs, articles, and wikis, designed to enhance user engagement and content accessibility. This platform allows users to interact dynamically and access a wealth of information seamlessly.',
                technologiesUsed: ['html', 'css', 'bootstrap', 'javascript', 'dotnet', 'jira', 'agile'],
                role: 'Constructed and styled web pages using HTML5 and CSS3, implementing advanced design techniques to enhance visual appeal and user experience while adhering to Agile methodologies. Added dynamic and interactive elements using JavaScript, significantly improving client-side functionality within an Agile framework for efficient workflow and timely updates.Utilized the .NET Framework for backend processes, integrating various components smoothly to ensure a cohesive user experience and maintaining Agile practices throughout development.'
            },
            {
                title: 'Project Green Bean',
                contentKey: '',
                technologiesUsed: ['hibernate', 'spring', 'mysql', 'node', 'angular', 'react'],
                role:'Acquired proficiency in technologies such as Spring Boot, Node.js, Angular, and React, completing over 15 projects and enhancing related efficiency by 20%. Built a task-tracking application for the company, improving task management and transparency by 30%, and revolutionized projects by integrating HTML, CSS, and Bootstrap, increasing user satisfaction by 25%. Identified and resolved over 50 software defects and bugs, ensuring high-quality deliverables and reducing post-release issues by 40%.'
            },
        ]
    }
    // {
    //     title: 'Software Developer Intern @ coMakeIT Software (Now Xebia)',
    //     contentKey: 'experience.experienceItems.intern.content',
    //     professionKey: 'experience.experienceItems.intern.profession',
    //     periodKey: 'experience.experienceItems.intern.period',
    //     lengthKey: 'experience.experienceItems.intern.length',
    //     url: 'https://website.xebia.com/digital-transformation/software-technology/product-engineering/',
    //     technologies: [
    //         'javascript', 'jquery','css',
    //         'bootstrap', 'postgresql', 'angular', 'spring','node','mysql','git'
    //     ]
    // }
;

</script>

<template>
    <section
        id="experience"
        class="experience"
    >
        <h2 :data-aos="FadeDown" class="title">{{ t('experience.title') }}</h2>

        <div class="items">
            <ExperienceItem
                :title="experienceItems.title"
                :content="t(experienceItems.contentKey)"
                :profession="t(experienceItems.professionKey)"
                :period="t(experienceItems.periodKey)"
                :length="t(experienceItems.lengthKey ?? '')"
                :technologies="experienceItems.technologies"
                :companyProjects="experienceItems.companyProjects"
                :animation="FadeRight"
            />
        </div>

    </section>
</template>

<style lang="less" scoped>
@import '@/styles/variables.less';

.experience {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 65%;
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
        pointer-events: none;
    }
}

@media (min-width: @first-breakpoint) {
    .experience {
        // min-width: 36rem;
        // max-width: 38rem;
        padding-bottom: 7rem;

        .title {
            min-height: 4rem;
        }
    }
}

</style>
