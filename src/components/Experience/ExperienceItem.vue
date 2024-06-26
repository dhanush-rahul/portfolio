<script setup lang="ts">
import TechnologyElement from '@/components/TechnologyElement.vue';
import ProjectItem from '@/components/Experience/ProjectItem.vue';
import { useCursorHover } from '@/directives/useCursorHover';
import { useThemeStore } from '@/stores/theme';
import { TechnologyType } from '@/types/TechnologyType';
import { AnimationType } from '@/types/AnimationType';
import { DarkTheme, LightTheme } from '@/constants/app';
import { computed } from 'vue';

const vCursorHover = useCursorHover();

const themeStore = useThemeStore();

const props = defineProps<{
    title: string,
    content: string,
    profession: string,
    period: string,
    length?: string,
    technologies: TechnologyType[],
    companyProjects:  {
    title: string;
    contentKey: string;
    technologiesUsed: TechnologyType[];
    role: string;
  }[],
    animation: AnimationType;
}>();

// const parsedProjects = computed(() => {

//     return props.companyProjects.map(project =>{
//         return{
//             ...project,
//             technologiesUsed: project.technologiesUsed.replace(/[\[\]]/g, '').split(',').map((tech: string) => tech.trim())
//         }
//     })
// });

</script>

<template>
    <div :data-aos="props.animation">
        <span
            class="link">
            <div
                class="experience-item"
                :class="{ 'experience-item-dark-theme': themeStore.theme === DarkTheme,
                      'experience-item-light-theme': themeStore.theme === LightTheme }"
            >
                <h3 class="title">{{ props.title }}</h3>

                <p class="content">
                    {{ props.content }}
                </p>
                <div class="projects">
                    <ProjectItem
                        v-for="(project, index) in props.companyProjects"
                        :key="index"
                        :title="project.title"
                        :content="project.contentKey"
                        :technologiesUsed="project.technologiesUsed"
                        :role="project.role"
                    />
                </div>

                <p class="below">
                    <span>{{ props.profession }}</span>
                    <div class="job-time">
                        <span>{{ props.period }}</span>
                        <span>{{ props.length }}</span>
                    </div>
                </p>
            </div>
        </span>
    </div>
</template>

<style lang="less" scoped>
@import '@/styles/variables.less';

.link {
    text-decoration: none;
    color: inherit;
}
.experience-item {
    display: flex;
    flex-direction: column;
    text-align: center;
    gap: 0.5rem;
    min-height: 10rem;
    width: 100%;
    border: solid @blue-color 0.2rem;
    border-radius: 1rem;
    padding: 0.6rem 0.9rem 0.6rem 0.9rem;
    margin-bottom: 1.5rem;
    cursor: pointer;

    transition: background-color ease @theme-switch-time;

    .title {
        display: flex;
        align-items: center;
        margin: auto;
        font-size: 1.4rem;
    }
    .content {
        display: flex;
        align-items: center;
        text-align: left;
        font-family: 'LatoFontLight', serif;
        font-style: italic;
        line-height: 1.3rem;
        font-size: 1.05rem;
    }
    .technologies {
        display: flex;
        align-content: flex-start;
        justify-content: center;
        flex-wrap: wrap;
        padding-top: 0.5rem;
        gap: 0.5rem;
    }
    .below {
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-family: 'LatoFontLight', serif;
        padding-top: 0.5rem;

        .job-time span {
            display: block;
        }
    }
}

@media (min-width: @first-breakpoint) {
    .experience-item {
        .title {
            max-width: 25rem;
        }
        .content {
            line-height: 1.4rem;
        }
        .technologies {
            justify-content: flex-start;
        }

        .below {
            .job-time span {
                display: inline;
            }
        }
    }
}

.experience-item-dark-theme {
    background-color: #dark[background-color-on-element];
}

.experience-item-light-theme {
    background-color: #light[background-color-on-element];
}

</style>
