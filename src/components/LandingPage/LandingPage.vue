<script setup lang="ts">
import AnimateSplitLetters from '@/components/LandingPage/AnimateSplitLetters.vue';
import { useLanguageSwitcher } from '@/composables/useLanguageSwitcher';
import { FadeUpRight } from '@/constants/app';

const { t } = useLanguageSwitcher();

</script>

<template>
    <section
        class="landing-page"
    >
        <div
            :data-aos="FadeUpRight"
            class="text"
        >
            <h2 class="my-name-is">{{ t('landingPage.myNameIs') }}</h2>

            <h2 class="name">
                <AnimateSplitLetters
                    :text="t('landingPage.name')"
                />
            </h2>

            <p class="description">{{ t('landingPage.description') }}</p>
        </div>
    </section>
</template>

<style lang="less" scoped>
@import '@/styles/variables.less';

.landing-page {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 65%;
    min-height: 60vh;
    margin: 0 auto;
    padding: 1.6rem;

    .text {
        .my-name-is {
            font-size: 1.7rem;
            font-family: 'FontCaveat', serif;
        }
        .name {
            display: block;
            margin-bottom: 0.5rem;
            font-family: 'LatoFontBold', serif;
            font-size: 3.5rem;
            color: @blue-color;
        }
        .description {
            font-size: 20px;
        }
    }
}

@media (min-width: @first-breakpoint) {
    .landing-page {
        // min-width: 30rem;
        // max-width: 40rem;
        min-height: calc(100vh - @navbar-height - @navbar-border);

        .text {
            .my-name-is {
                font-size: 2.5rem;
            }
            .name {
                font-size: 5rem;
            }
            .description {
                font-size: 20px;
            }
        }
    }
}

</style>
