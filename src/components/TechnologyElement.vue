<script setup lang="ts">
import { Icon } from '@iconify/vue';
import { useThemeStore } from '@/stores/theme';
import { TechnologyType } from '@/types/TechnologyType';
import { DarkTheme, LightTheme } from '@/constants/app';

const themeStore = useThemeStore();

type TechnologyConfigType = {
    title: string,
    icon: string
    width: number
}
type TechnologiesType = {
    [key in TechnologyType]: TechnologyConfigType;
};

const props = defineProps<{
    element: keyof TechnologiesType
}>();

const technologies: TechnologiesType = {
    php: {
        title: 'PHP',
        icon: 'logos:php',
        width: 48
    },
    laravel: {
        title: 'Laravel',
        icon: 'logos:laravel',
        width: 40
    },
    javascript: {
        title: 'JavaScript',
        icon: 'skill-icons:javascript',
        width: 35
    },
    jquery: {
        title: 'jQuery',
        icon: 'mdi:jquery',
        width: 42
    },
    sass: {
        title: 'Sass',
        icon: 'vscode-icons:file-type-sass',
        width: 42
    },
    less: {
        title: 'less',
        icon: 'logos:less',
        width: 42
    },
    bootstrap: {
        title: 'Bootstrap',
        icon: 'akar-icons:bootstrap-fill',
        width: 42
    },
    mysql: {
        title: 'MySQL',
        icon: 'logos:mysql',
        width: 52
    },
    postgresql: {
        title: 'PostgreSQL',
        icon: 'logos:postgresql',
        width: 42
    },
    git: {
        title: 'Git',
        icon: 'bi:git',
        width: 38
    },
    github: {
        title: 'GitHub',
        icon: 'akar-icons:github-fill',
        width: 38
    },
    python: {
        title: 'Python',
        icon: 'logos:python',
        width: 40
    },
    csharp: {
        title: 'C#',
        icon: 'vscode-icons:file-type-csharp2',
        width: 44
    },
    vue: {
        title: 'VueJS',
        icon: 'logos:vue',
        width: 38
    },
    redis: {
        title: 'Redis',
        icon: 'logos:redis',
        width: 40
    },
    pygame: {
        title: 'pygame',
        icon: 'noto:snake',
        width: 40
    },
    pyqt5: {
        title: 'PyQt5',
        icon: 'logos:qt',
        width: 40
    },
    pwa: {
        title: 'PWA',
        icon: 'logos:pwa',
        width: 36
    },
    html:{
        title: 'HTML',
        icon: 'logos:html-5',
        width: 30
    },
    css: {
        title: 'CSS',
        icon: 'logos:css-3',
        width: 30
    },
    java: {
        title: 'Java',
        icon: 'logos:java',
        width: 30
    },
    symfony: {
        title: 'Symfony',
        icon: 'logos:symfony',
        width: 40
    },
    docker: {
        title: 'Docker',
        icon: 'logos:docker-icon',
        width: 48
    },
    phpunit: {
        title: 'PHPUnit',
        icon: 'vscode-icons:file-type-phpunit',
        width: 38
    },
    typescript: {
        title: 'TypeScript',
        icon: 'skill-icons:typescript',
        width: 35
    },
    microservices: {
        title: 'Microservices',
        icon: 'carbon:microservices-1',
        width: 35
    },
    rabbitmq: {
        title: 'RabbitMQ',
        icon: 'logos:rabbitmq-icon',
        width: 30
    },
    tailwind: {
        title: 'Tailwind',
        icon: 'logos:tailwindcss-icon',
        width: 33
    },
    c: {
        title: 'C',
        icon: 'logos:c',
        width: 33
    },
    linux: {
        title: 'Linux',
        icon: 'flat-color-icons:linux',
        width: 41
    },
    react:{
        title:'React',
        icon:'logos:react',
        width: 30
    },
    spring:{
        title: 'Spring Boot',
        icon:'logos:spring',
        width: 40
    },
    angular:{
        title: 'Angular',
        icon: 'logos:angular',
        width: 30
    },
    next:{
        title: 'Next.js',
        icon: 'logos:nextjs',
        width: 30
    },
    reactnative:{
        title: 'React Native',
        icon: 'logos:react',
        width: 30
    },
    node:{
        title: 'Node.js',
        icon: 'logos:nodejs',
        width: 30
    },
    express:{
        title: 'Express.js',
        icon: 'logos:express',
        width: 30
    },
    r:{
        title: 'R',
        icon: 'logos:r',
        width: 20
    },
    kotlin:{
        title: 'Kotlin',
        icon: 'logos:kotlin',
        width: 30
    },
    android:{
        title: 'Android',
        icon: 'logos:android',
        width: 20
    },
    cplus:{
        title: 'C++',
        icon: 'logos:c++',
        width: 15,
    },
    redux: {
        title: 'Redux',
        icon: 'logos:redux',
        width: 30
    },
    ruby: {
        title: 'Ruby',
        icon: 'logos:ruby',
        width: 30
    },
    graphql: {
        title: 'GraphQL',
        icon: 'logos:graphql',
        width: 30
    },
    ci_cd: {
        title: 'CI/CD',
        icon: 'logos:jenkins', // Assuming Jenkins as a CI/CD icon, replace with a more fitting one if needed
        width: 30
    },
    postman: {
        title: 'Postman',
        icon: 'logos:postman',
        width: 30
    },
    jira: {
        title: 'Jira',
        icon: 'logos:jira',
        width: 30
    },
    agile: {
        title: 'Agile',
        icon: 'fa-brands:gitlab',
        width: 30
    },
    bitbucket:{
        title: 'Bitbucket',
        icon: 'logos:bitbucket',
        width: 30
    },
    ml:{
        title: 'Machine Learning',
        icon: 'mdi:brain',
        width: 30
    },
    dotnet: {
        title: '.NET Framework',
        icon: 'logos:dotnet',
        width: 30
    },
    hibernate: {
        title: 'Hibernate',
        icon: 'logos:hibernate',
        width: 40
    },
};

</script>

<template>
    <div
        class="technology-element"
        :class="{ 'technology-element-dark-theme': themeStore.theme === DarkTheme,
                  'technology-element-light-theme': themeStore.theme === LightTheme }"
    >

        <div class="icon">
            <Icon
                :icon="technologies[props.element].icon"
                :width="technologies[props.element].width"
            />
        </div>

        <span class="title">{{ technologies[props.element].title }}</span>

    </div>
</template>

<style lang="less" scoped>
@import '@/styles/variables.less';

.technology-element {
    display: flex;
    align-items: center;
    min-height: 3.2rem;
    padding: 0.2rem;
    border: solid @blue-color 0.1rem;
    border-radius: 1rem;

    transition: background-color ease @theme-switch-time;

    .icon {
        display: flex;
        align-items: center;
        padding-left: 0.5rem;
    }
    .title {
        padding: 0.5rem;
    }
}

.technology-element-dark-theme {
    color: #dark[text-color];
    background-color: #dark[background-color-on-element];
}

.technology-element-light-theme {
    color: #light[text-color];
    background-color: #light[background-color-on-element];
}

</style>
