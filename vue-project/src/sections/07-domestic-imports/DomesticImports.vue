<script setup>
import CopyBlock from '../../components/layout/CopyBlock.vue'
import SectionGrid from '../../components/layout/SectionGrid.vue'
import StorySection from '../../components/story/StorySection.vue'
import DistrictDonutsVisual from './DistrictDonutsVisual.vue'

defineProps({
  minimalMode: {
    type: Boolean,
    default: false,
  },
})
</script>

<template>
  <StorySection id="domestic-imports" height="min-screen" width="full">
    <SectionGrid class="domestic-imports-grid" :columns="12" gap="1.25rem" align="start">
      <div v-if="!minimalMode" class="story-copy story-copy--top">
        <CopyBlock title="">
          <p>
            Very little of this complexity shows up on your plate.
          </p>
          <p>
            For a cuisine so heavily tied to the cultural image of Japan, bluefin tuna consumed in sushi worldwide may have very little to do with the country. The total share of global bluefin production from Japan has decreased, as other countries — especially those around the Mediterranean — make strides in bluefin tuna aquaculture. If running at full capacity, farms registered with ICCAT in the Mediterranean have the capacity to produce nearly 80,000 tonnes of bluefin tuna per year. Most bluefin consumed in the United States doesn’t come from Japanese waters, nor does it travel through Japanese fish markets.
          </p>
          
        </CopyBlock>
      </div>
      <div class="domestic-visual">
        <DistrictDonutsVisual />
      </div>
      <div v-if="!minimalMode" class="story-copy story-copy--bottom">
        <CopyBlock title="">
          <p>
            The origin of bluefin tuna varies from city to city in the United States. Most cities import a large proportion of their bluefin from Spain, likely from farms near Murcia. In San Diego, nearly 100% of imported bluefin comes from Mexico, specifically ranches on the Pacific coast of Baja California. Portland, Maine, is the destination of choice for Canadian-caught bluefin. If you want Japanese — or even just Pacific caught or farmed bluefin tuna — your best bet is to go to Honolulu.
          </p>
          <p>
            In short, an answer to the original question: thanks to aggressive fisheries management
practices and the development of tuna aquaculture, the world is not running out of bluefin tuna,
and subsequently are not close to running out of bluefin tuna sushi. The peaks and valleys of
global bluefin tuna catch closely cleave to the peaks and valleys of the demand for sushi, and
will likely continue to do so in the near future. The advancement of bluefin tuna aquaculture,
despite questions about its sustainability, has created enough supply of bluefin that bluefin
harvest has returned to historical levels. This advancement, as well as changing patterns of
bluefin distribution, have resulted in different countries (especially Mediterranean countries)
becoming vital in bluefin production, as well as Japan’s reduced importance as a producer of
bluefin.
          </p>
          <p>
            There is no last sushi in the world. For now.
          </p>
        </CopyBlock>
      </div>
    </SectionGrid>
  </StorySection>
</template>

<style scoped>
.domestic-imports-grid {
  min-height: 100vh;
  align-items: center;
}

.domestic-visual {
  grid-column: 1 / span 12;
  padding-bottom: clamp(2rem, 6vh, 5rem);
}

@media (max-width: 900px) {
  .domestic-imports-grid {
    min-height: auto;
  }

  .domestic-visual {
    grid-column: 1 / -1;
    min-height: 100vh;
    min-height: 100dvh;
    display: flex;
    align-items: center;
    padding-bottom: 0;
  }

  .domestic-visual > * {
    width: 100%;
  }
}
</style>
