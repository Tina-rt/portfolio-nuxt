<script setup lang="ts">
import type { IndexCollectionItem } from '@nuxt/content'

defineProps<{
    page: IndexCollectionItem
}>()
</script>

<template>
    <UPageSection :title="page.skills.title" :ui="{
        container: 'px-0 !pt-0 sm:gap-6 lg:gap-8',
        title: 'text-left text-xl sm:text-xl lg:text-2xl font-medium'
    }">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div v-for="(category, index) in page.skills.categories" :key="index" class="flex flex-col gap-4">
                <h3 class="text-sm font-semibold text-muted uppercase tracking-wider">
                    {{ category.title }}
                </h3>
                <div class="flex flex-wrap gap-2">
                    <Motion v-for="(skill, skillIndex) in category.items" :key="skillIndex"
                        :initial="{ opacity: 0, scale: 0.9 }" :while-in-view="{ opacity: 1, scale: 1 }"
                        :transition="{ delay: 0.1 * (index + skillIndex), duration: 0.4 }"
                        :in-view-options="{ once: true }">
                        <div
                            class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-muted/50 border border-muted/50 hover:bg-muted transition-colors group">
                            <UIcon :name="skill.icon"
                                class="size-4 text-muted group-hover:text-primary transition-colors" />
                            <span class="text-sm font-medium">{{ skill.name }}</span>
                        </div>
                    </Motion>
                </div>
            </div>
        </div>
    </UPageSection>
</template>
