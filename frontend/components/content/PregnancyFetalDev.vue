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
          <v-card-text>
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
          content: 'After fertilisation, the embryo is implanted in the uterus and vital organs begin to form. By week 5, the heart starts beating. The brain, spinal cord, and limbs begin to take shape, and by the end of the first trimester, the fetus has recognisable features like fingers, toes, and facial contours. Though still tiny, it\'s already moving—though the mother can\'t feel it yet.'
        },
        // TODO: ?can link here to anatomy scan, diabetes screening.  Need to check the growth of baby (tapemeasurement uss growth)
        {
          title: 'Second Trimester (or months 4-6)',
          description: 'Weeks 13-26',
          icon: 'mdi-baby-bottle-outline',
          content: 'With the foundations of the placenta laid down and maternal blood flow bringing more nutrients and oxygen to the placenta, your baby gets bigger and you will be able to see more features on scan. Around week 20, many mothers feel the first movements of their baby. Organs like the lungs and digestive system mature, and the sex of the baby can often be determined from an ultrasound scan. '
        },
        // TODO: Growth scans as needed
        {
          title: 'Third Trimester (or months 7-9)',
          description: 'Weeks 27-40',
          icon: 'mdi-baby',
          content: 'This stage is all about growth and fine-tuning. The brain develops rapidly, fat accumulates under the skin, and the lungs prepare for breathing. The baby responds to sounds and light. As space in the uterus becomes more constrained, the baby will usually naturally turn to a position of \'best fit\' with its head is facing downwards, ready for birth.'
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
