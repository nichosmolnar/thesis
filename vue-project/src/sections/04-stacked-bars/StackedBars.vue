<script setup>
import CopyBlock from '../../components/layout/CopyBlock.vue'
import SectionGrid from '../../components/layout/SectionGrid.vue'
import PinnedScrollSection from '../../components/story/PinnedScrollSection.vue'
import StorySection from '../../components/story/StorySection.vue'
import TunaStackedBarsVisual from './TunaStackedBarsVisual.vue'

defineProps({
  minimalMode: {
    type: Boolean,
    default: false,
  },
})

const steps = [
  {
    id: 'chart-intro',
    title: 'Here is the bar chart.',
    text: 'Each column is a year of global tuna catch. Scroll to watch the series build.',
    visible: false,
  },
  {
    id: 'hf1',
    title: '',
    text: "As sushi's popularity grew, so did the demand for bluefin tuna. In the 1980s, it became possible and profitable to ship Atlantic bluefin tuna to Japan.",
    visible: true,
  },
  {
    id: 'hf1a',
    title: '',
    text: 'This reliance on Japan was a double-edged sword: the decline of the Japanese economy towards the 1990s marked a decrease in demand for bluefin tuna and a resulting decline in catch.',
    visible: true,
  },
  {
    id: 'hf1b',
    title: '',
    text: 'Yet changes in sushi culture (conveyer belt sushi and the spread of sushi overseas) led to resurgent catch numbers. By 2007, over 60,000 tonnes of Atlantic bluefin tuna were caught yearly.',
    visible: true,
  },
  {
    id: 'hf2',
    title: '',
    text: 'Two years later, the global catch had fallen by 80%. Not for any change in demand — sushi remained popular - but a historic level of overfishing. The population was at risk of complete collapse. Strict management measures were put in place.',
    visible: true,
  },
  {
    id: 'hf2-linger',
    title: '',
    text: 'This is where the story of Bluefin tuna is stuck.',
    visible: true,
  },
  {
    id: 'hf3',
    title: '',
    text: "Yet slowly, the stock has recovered. Atlantic bluefin has moved from Endangered to Least Concern status, and quotas have increased. There is no immediate risk of a stock collapse, and so no immediate risk of a type of sushi wiped from existence.",
    visible: true,
  }
]
</script>

<template>
  <StorySection id="stacked-bars" height="overscroll" width="full">
    <SectionGrid v-if="!minimalMode" class="stacked-bars-lead-grid" :columns="12" gap="1.25rem" align="start">
      <div class="story-copy story-copy--top">
        <CopyBlock title="Bluefin Tuna was on the brink of extinction.">
          <p>
            You might associate Bluefin tuna with the panda, the tigers, the blue whale — charismatic megafauna at serious risk of extinction, with diminishingly small populations and few remaining wild members. And for a few years, this was an apt association: bluefin tuna were pushed to the brink by human fishing pressure as populations teetered on the brink. 
          </p>
          <p>
            How then, in 2023, can a single fish market consume nearly 2000 tonnes of top-grade bluefin tuna, if this population is on the edge of collapsing?
          </p>
          <p>
            The story of Bluefin tuna is a story stuck in a specific place — that is, 2007. Bluefin tuna’s image as the endangered megafauna, the poster-child for overfishing practices, does not do this fish justice. There was a time and place where the most heavily fished bluefin populations were not recovering year after year, and without the proper course correction the oceans may very well have run out of the fish. However, this image does not adequately represent the current state of tuna. 
          </p>
          <p>
            Without the proper context, it can be hard to understand the scale of a 2000 tonnes, or 8,060 individual tuna, or even the 156 tuna consumed each week at the Tokyo Fish Market. These are a drop in the ocean of tuna consumption. The bluefin tuna trade is not the largest fish market in the world by volume (it’s not even the largest tuna market in the world by volume), yet it is one of the most lucrative.
          </p>
          <p>
            This is driven almost primarily by demand for sushi. The modern sushi trade is supported by a massive and highly global network of fishermen and distributors. No fish best represents the modern sushi industry as tuna. It is the most popular, most expensive, and most consistent ingredient for the cuisine. Most if not all high-grade tuna caught in the world is used for sushi. 
          </p>
          <p>
            The sushi industry has turned tuna into a junk fish caught with little commercial value into one of the most expensive cuts of meat in the world. Tuna is so valuable and the margins are so high that a fish caught off the coast of Massachusetts can be flown to Tokyo, priced, and sold to a sushi restaurant in Boston. In its early history, sushi was shaped by what fish was seasonally available and local enough that it could be made without spoilage. Sushi in the modern day warps global fishing fleets to its wants and needs.
          </p>
          <p>
            How did we get here?
          </p>
        </CopyBlock>
      </div>
    </SectionGrid>
    <div class="stacked-bars-scrolly">
      <PinnedScrollSection :steps="steps" :scroll-offset="0.72">
        <template #graphic="graphicProps">
          <TunaStackedBarsVisual :active-step="graphicProps.activeStep" />
        </template>
        <template #step="{ step }">
          <CopyBlock v-if="!minimalMode && step.visible !== false" :title="step.title">
            <p style="white-space: pre-line">{{ step.text }}</p>
          </CopyBlock>
          <span v-else-if="minimalMode" class="stacked-bars-step-slot" aria-hidden="true" />
        </template>
      </PinnedScrollSection>
    </div>
  </StorySection>
</template>

<style scoped>
.stacked-bars-lead-grid {
  width: 100%;
  padding-bottom: clamp(1rem, 4vh, 2.5rem);
}

.stacked-bars-scrolly {
  width: 100%;
}

.stacked-bars-lead {
  min-height: clamp(5rem, 26vh, 16rem);
  pointer-events: none;
}

.stacked-bars-step-slot {
  display: block;
  width: 0;
  height: 0;
  overflow: hidden;
  visibility: hidden;
  pointer-events: none;
}

#stacked-bars :deep(.sticky-graphic) {
  background: var(--color-section-surface);
  display: flex;
  align-items: center;
}

#stacked-bars :deep(.sticky-graphic > *) {
  width: 100%;
}
</style>
