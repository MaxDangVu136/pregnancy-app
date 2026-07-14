<template>
  <div class="fetal-development-timeline">
    <img style='width: 50%; margin: 0 auto; display: block; padding-bottom: 20px;' src='https://pregnancy-app-tau.vercel.app/static/images/placeholder.png' alt='Fetal Development' />
    <v-timeline
      :reverse="false"
      dense
    >
      <v-timeline-item
        v-for="item in fetalDevelopment"
        :key="item.title"
      >
        <template v-slot:icon>
          <v-icon color="white">{{ item.icon }}</v-icon>
        </template>
        <v-card class="elevation-2">
          <v-card-title class="text-h5">
            {{ item.title }}
          </v-card-title>
          <v-card-subtitle>
            {{ item.description }}
          </v-card-subtitle>
          <v-card-text style="white-space: pre-line;">
            {{ item.content }}
          </v-card-text>
        </v-card>
      </v-timeline-item>
    </v-timeline>
  </div>
</template>

<script>
export default {
  name: 'PregnancyFetalDev',
  data() {
    return {
      fetalDevelopment: [
        // TODO: ?can link to tests done at this stage? Important t to find a midwife, blood tests , offered screening for conditions where there are chromosome differences
        {
          title: 'First Trimester',
          description: 'Weeks 1-12 (or months 1-3)',
          icon: 'mdi-baby-face-outline',
          content: 'After fertilisation, the embryo is implanted in the uterus and vital organs begin to form. \n\nBy week 5, the heart starts beating and the brain, spinal cord, and limbs begin to take shape. By week 9, the embryo has developed into a fetus. \n\nAt the end of the first trimester, the fetus has recognisable features like fingers, toes, and facial contours. The fetus is already moving but the mother can\'t feel this yet.'
        },
        // TODO: ?can link here to anatomy scan, diabetes screening.  Need to check the growth of baby (tapemeasurement uss growth)
        {
          title: 'Second Trimester',
          description: 'Weeks 13-26 (or months 4-6)',
          icon: 'mdi-baby-bottle-outline',
          content: 'The foundations of the placenta are laid down, allowing blood flow to bring more nutrients and oxygen from mum to the fetus. The developing fetus gets bigger and you can see more features on the scan. \n\nAround week 20, many mothers feel the first movements of their baby-to-be. Organs like the lungs and digestive system mature, and the sex of the future baby can be determined from an ultrasound scan. '
        },
        // TODO: Growth scans as needed
        {
          title: 'Third Trimester',
          description: 'Weeks 27-40 (or months 7-9)',
          icon: 'mdi-baby',
          content: 'This stage is all about growth and fine-tuning of the fetus. \n\nThe brain develops rapidly, fat accumulates under the skin, and the lungs prepare for breathing. The fetus responds to sounds and light. \n\nAs space in the uterus becomes smaller for the growing fetus, it naturally turns to a position of \'best fit\'. Here, the head faces downwards, getting ready for birth.'
        }
      ]
    }
  }
}

</script>

<style scoped lang="scss">
.fetal-development-timeline {
  padding: 20px;
  max-width: 800px;
  margin: 0 auto;
}

::v-deep .v-timeline {
  padding-top: 0;
}

::v-deep .v-timeline-item__dot {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

::v-deep .v-card {
  border-radius: 12px;
  transition: all 0.3s ease;
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15) !important;
  }
}

::v-deep .v-timeline-item__opposite {
  padding-right: 24px;
  
  @media (max-width: 959px) {
    padding-right: 16px;
  }
}

.text-h6 {
  margin-bottom: 4px;
}

.text-subtitle-1 {
  font-weight: 500;
}

@media (max-width: 599px) {
  .fetal-development-timeline {
    padding: 16px;
  }
  
  ::v-deep .v-timeline-item__opposite {
    min-width: 120px;
  }
}
</style>
