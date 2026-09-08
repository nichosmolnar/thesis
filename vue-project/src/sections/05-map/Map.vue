<script setup>
import CopyBlock from '../../components/layout/CopyBlock.vue'
import SectionGrid from '../../components/layout/SectionGrid.vue'
import PinnedScrollSection from '../../components/story/PinnedScrollSection.vue'
import StorySection from '../../components/story/StorySection.vue'
import MapSectionVisual from './MapSectionVisual.vue'

defineProps({
  minimalMode: {
    type: Boolean,
    default: false,
  },
})

/** Scroll steps drive `activeStep` only; all copy lives on the map HUD in MapSectionVisual. */
const steps = [
  // 0–4: year animates 1965 → 2023 (global view)
  { id: 'm1', title: '', text: '', visible: true },
  { id: 'm2', title: '', text: '', visible: true },
  { id: 'm3', title: '', text: '', visible: true },
  { id: 'm4', title: '', text: '', visible: true },
  { id: 'm5', title: '', text: '', visible: true },
  // 5–8: global 2023 linger (basin cue on HUD)
  { id: 'm8', title: '', text: '', visible: true },
  // 9: zoom into Mediterranean, year stays 2023 (no regional year scrub)
  { id: 'm10', title: '', text: '', visible: true },
  // 10–11: farm dots fade in, then single linger beat; still Med camera
  { id: 'm11', title: '', text: '', visible: true },
  { id: 'm12', title: '', text: '', visible: true },
  // 12–14: return to global + end padding (year stays 2023)
  { id: 'm13', title: '', text: '', visible: true },
  { id: 'm14', title: '', text: '', visible: true },
]
</script>

<template>
  <StorySection id="map" height="overscroll" width="full">
    <SectionGrid v-if="!minimalMode" class="map-lead-grid" :columns="12" gap="1.25rem" align="start">
      <div class="story-copy story-copy--top">
        <CopyBlock title="Why?">
          <p>
            The sushi industry did not slow down even as bluefin tuna catches dwindled. In the years of diminished wild catches, there is no evidence there was a noticeable effect on the supply to the sushi industry. Bluefin tuna, it seems, was still being sold in sushi restaurants around the world.
          </p>
          <p>
            How is this possible?
          </p>
          <p>
            If you slice the data another way, adding a geographical element not represented by a bar chart, hidden patterns reveal themselves.
          </p>
          <p>
            The world’s oceans are not created equal, at least in the eyes of the bluefin tuna. The three major subspecies of bluefin — the Southern, Atlantics, and Pacific bluefin — live distinct, separated regions of the ocean. All three favor temperate oceans: the Southern population prefers the waters near Australia and New Zealand, the Atlantic population reaches from the Mediterranean to the Eastern United States, and the mighty Pacific population spans from Japanese waters all the way to Baja California, Mexico.
          </p>
        </CopyBlock>
      </div>
    </SectionGrid>
    <PinnedScrollSection :steps="steps" :scroll-offset="0">
      <template #graphic="graphicProps">
        <MapSectionVisual
          :active-step="graphicProps.activeStep"
          :step-progress="graphicProps.stepProgress"
          :step-count="steps.length"
          :minimal-mode="minimalMode"
        />
      </template>
      <template #step>
        <!-- Non-empty slot suppresses PinnedScrollSection default .step-card fallback. -->
        <span class="map-step-slot" aria-hidden="true" />
      </template>
    </PinnedScrollSection>
  </StorySection>
</template>

<style scoped>
.map-lead-grid {
  width: 100%;
  padding-bottom: clamp(1rem, 4vh, 2.5rem);
}

:deep(#map.story-section) {
  padding-bottom: 32px;
}

#map :deep(.sticky-graphic) {
  background: var(--color-default-blue);
}

#map :deep(.step-column) {
  /* Delay first step activation until map has fully pinned. */
  padding-top: 90vh;
  /* Keep map pinned until the final step reaches the top. */
  padding-bottom: 90vh;
}

#map :deep(.scroll-step) {
  padding: 0;
  background: transparent;
  border: none;
  box-shadow: none;
}

#map :deep(.scroll-step.active) {
  background: transparent;
  box-shadow: none;
}

/* Default slot fallback .step-card uses PinnedScrollSection scoped styles — hide entirely here. */
#map :deep(.step-card) {
  display: none !important;
}

#map :deep(.map-step-slot) {
  display: block;
  width: 0;
  height: 0;
  overflow: hidden;
  visibility: hidden;
  pointer-events: none;
}

@media (max-width: 900px) {
  #map :deep(.step-column) {
    padding-top: 100vh;
    padding-bottom: 100vh;
  }
}
</style>
