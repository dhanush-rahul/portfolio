<script setup lang="ts">
import ExperienceItem from '@/components/Experience/ExperienceItem.vue';
import { useLanguageSwitcher } from '@/composables/useLanguageSwitcher';
import { TechnologyType } from '@/types/TechnologyType';
import { FadeDown, FadeLeft, FadeRight } from '@/constants/app';

const { t } = useLanguageSwitcher();

type Experience = {
    title: string,
    contentKey: string,
    professionKey: string,
    periodKey: string,
    lengthKey?: string,
    url: string,
    technologies: TechnologyType[]
};

const experienceItems: Experience[] = [
    {
        title: 'Associate Software Developer @ coMakeIT Software (Now Xebia)',
        contentKey: 'experience.experienceItems.associate.content',
        professionKey: 'experience.experienceItems.associate.profession',
        periodKey: 'experience.experienceItems.associate.period',
        lengthKey: 'experience.experienceItems.associate.length',
        url: 'https://website.xebia.com/digital-transformation/software-technology/product-engineering/',
        technologies: [
            'microservices', 'git',
            'react', 'spring', 'angular', 'next', 'reactnative', 'java', 'javascript', 'jquery','postgresql', 'node', 'express'
        ]
    },
    {
        title: 'Software Developer Intern @ coMakeIT Software (Now Xebia)',
        contentKey: 'experience.experienceItems.intern.content',
        professionKey: 'experience.experienceItems.intern.profession',
        periodKey: 'experience.experienceItems.intern.period',
        lengthKey: 'experience.experienceItems.intern.length',
        url: 'https://website.xebia.com/digital-transformation/software-technology/product-engineering/',
        technologies: [
            'javascript', 'jquery','css',
            'bootstrap', 'postgresql', 'angular', 'spring','node','mysql','git'
        ]
    }
];

</script>

<template>
    <section
        id="experience"
        class="experience"
    >
        <h2 :data-aos="FadeDown" class="title">{{ t('experience.title') }}</h2>

        <div class="items">
            <ExperienceItem
                v-for="(experience, index) in experienceItems"
                :key="index"
                :title="experience.title"
                :content="t(experience.contentKey)"
                :profession="t(experience.professionKey)"
                :period="t(experience.periodKey)"
                :length="t(experience.lengthKey ?? '')"
                :url="experience.url"
                :technologies="experience.technologies"
                :animation="index % 2 === 0 ? FadeRight : FadeLeft"
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
    min-width: 100%;
    margin: auto;
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
    .experience {
        min-width: 36rem;
        max-width: 38rem;
        padding-bottom: 7rem;

        .title {
            min-height: 4rem;
        }
    }
}

</style>
