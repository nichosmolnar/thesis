<script setup>
import CopyBlock from '../../components/layout/CopyBlock.vue'
import SectionGrid from '../../components/layout/SectionGrid.vue'
import StorySection from '../../components/story/StorySection.vue'
import TunaProductionStreamgraphVisual from './TunaProductionStreamgraphVisual.vue'

defineProps({
  minimalMode: {
    type: Boolean,
    default: false,
  },
})
</script>

<template>
  <StorySection id="country-production" height="min-screen" width="full">
    <div class="country-production-shell">
      <SectionGrid class="country-production-grid" :columns="12" gap="1.25rem" align="start">
        <div v-if="!minimalMode" class="story-copy story-copy--top">
          <CopyBlock title="To Ranch a Tuna">
            <p>
              The sushi industry avoided disruption by the advent of bluefin tuna farming. By 2010 — at the start of the catch limitations — 31.6% of bluefin tuna produced worldwide was farmed. As of 2023, 50% of the global bluefin catch is produced in farms. Aquaculture—fish farming, or in the case of bluefin “fish ranching” — smoothed over gaps in supply.
            </p>
            <p>
              Each of these three species of tuna has a now-robust ranching industry. Ranching the Atlantic bluefin tuna is concentrated off the coast of the United States, Europe, and the Mediterranean Sea. Southern bluefin tuna farming is concentrated in Australia, while Pacific bluefin tuna farming is concentrated in Japan and in Baja California, Mexico.
            </p>
            <p>
              Most farmed tuna are produced via tuna ranching or penning, where young fish are captured in the wild and raised to captivity in near-shore and open ocean pens.This practice allows for finer control of each year’s harvest. Yet tuna penning has issues and inefficiencies, with a long road ahead to become a truly sustainable practice. Tuna are often caught vast distances away from their long-term penning locations. Fishermen can lose up to 40% of their catch in transit. Bluefin tuna penning still contributes to the overfishing of tuna populations and introduces new fishing pressures onto other fish stocks, which are caught as feed for penned tuna.
            </p>
            <p>
              Tuna has relatively high feed conversion ratios: more animal protein (usually fish from low-value fisheries, such as herring, sardines, or mackerel) is needed to fatten tuna than the tuna eventually ends up producing. It takes 3 kg of wild fish to produce 1 kg of farmed salmon (i.e., a 3:1 ratio). For farmed cod the ratio is 5:1; For ranched tuna, the ratio reaches 20:1.
            </p>
            <p>
              Despite these challenges, tuna ranching is the likely future of the bluefin tuna industry.
            </p>
          </CopyBlock>
        </div>
        <div class="production-visual">
          <TunaProductionStreamgraphVisual />
        </div>
      </SectionGrid>
    </div>
  </StorySection>
</template>

<style scoped>
.country-production-shell {
  min-height: 100vh;
  display: flex;
  align-items: center;
  width: 100%;
}

.country-production-grid {
  width: 100%;
}

.production-visual {
  grid-column: 1 / span 12;
}

@media (max-width: 900px) {
  .production-visual {
    grid-column: 1 / -1;
    min-height: 100vh;
    min-height: 100dvh;
    display: flex;
    align-items: center;
    min-width: 0;
    max-width: 100%;
  }

  .production-visual > * {
    width: 100%;
    max-width: 100%;
    min-width: 0;
  }
}
</style>
