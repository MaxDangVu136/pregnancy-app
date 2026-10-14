<template>
  <div>
    <v-card class="timeline-card">
      <v-card-text class="content-text">
        <p>You may have a scan at 5-6 weeks of gestation when medical reasons or health risk factors are present. The scan aims to:</p>
        <ul>
          <li>
            Check the location of the pregnancy (that it is in the uterus and
            not
            <v-btn
              text
              small
              color="primary"
              class="medical-term-btn"
              @click="showEctopicDialog = true"
            >
              ectopic</v-btn
            >).
          </li>
        </ul>
      </v-card-text>
    </v-card>
    <v-card class="timeline-card">
      <v-card-text class="content-text">
        <p>
          At 12 weeks of gestation, this is often the first scan as part of standard pregnancy care. 
          The scan aims to:
        </p>
        <ul>
          <li>Determine if there is a single pēpi or twins/triplets.</li>
          <li>Check the basic anatomy of the fetus.</li>
          <li>Listen to the fetal heartbeat.</li>
          <li>
            Screen for chromosomal conditions using
            <v-btn
              text
              small
              color="primary"
              class="medical-term-btn"
              @click="showNuchalDialog = true"
            >
              nuchal translucency
            </v-btn>. 
          </li>
        </ul>
      </v-card-text>
    </v-card>

    <v-card class="timeline-card">
      <!--TODO Could also add in here about checking blood flow to the placenta / uterine artery dopplers  -->
      <!-- TODO: Link to doppler ultrasound in pregnancy after "How easily blood is flowing to the placenta" -->
      <v-card-text class="content-text">
        <p>At 20 weeks of gestation, you will have another scan that checks on the following:</p>
        <ul>
          <li>How the pēpi is growing and developing, which is indicated by estimating the
            <v-btn
              text
              small
              color="primary"
              class="medical-term-btn"
              @click="showFetalWeightDialog = true"
            >
              fetal weight
            </v-btn>.
          </li>
          <li>The anatomy of all the major organs.</li>
          <li>That the limbs have formed (arms, legs, hands and feet), and if any movement can be seen.</li>
          <li>How the heart is beating.</li>
          <li>How easily blood is flowing to the placenta.</li>
          <li>The amount of fluid around your pēpi. Low levels of amniotic fluid can be an indicator of pregnancy complications.</li>
          <li>Where the placenta is growing.</li>
        </ul>
      <figure class="figure-group"; style='text-align: center;'>
        <figure class="subfigure">
          <img :src="getImagePath('/img/ultrasound/fetal-development_us/limbs/Week20_71_feet.jpg')" alt='20-week ultrasound scan showing the feet.' style='width: 50%; max-width: 700px; margin: 20px auto; display: block;' />
          <figcaption>Feet of pēpi</figcaption>
        </figure>
        <figure class="subfigure">
          <img :src="getImagePath('/img/ultrasound/fetal-development_us/organs/Week20_57_4_chamber_heart.gif')" alt='20-week ultrasound scan showing the heart beating.' style='width: 50%; max-width: 700px; margin: 20px auto; display: block;' />
          <figcaption>Beating heart of pēpi</figcaption>
        </figure>
        <figcaption><small>Examples of a 20 week ultrasound scan of the pēpi, with key body parts labelled in <strong>red</strong>. &copy; 2025 James Lab & Pregnancy Modelling Group. All rights reserved.</small></figcaption>
      </figure>
       </v-card-text>
    </v-card>

    <!-- Ectopic Pregnancy Dialog -->
    <v-dialog v-model="showEctopicDialog" max-width="500" persistent>
      <v-card>
        <v-card-title class="headline">
          <v-icon left color="warning"
            >mdi-information-variant-circle-outline</v-icon
          >
          Ectopic Pregnancy
        </v-card-title>

        <v-card-text class="pt-4">
          <p>
            An ectopic pregnancy occurs when a fertilized egg implants outside
            the uterus, most often in a fallopian tube. This can be dangerous
            and requires prompt medical attention.
          </p>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="showEctopicDialog = false">
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <!-- Nuchal Translucency Dialog  -->
    <v-dialog v-model="showNuchalDialog" max-width="500" z-index="1000" persistent>
      <v-card>
        <v-card-title class="headline">
          <v-icon left color="info">mdi-ruler</v-icon>
          Nuchal Translucency
        </v-card-title>

        <v-card-text class="pt-4">
          This is a measurement of the thickness of fluid at the back of the
          pēpi’s neck that is used in combination with a blood test to screen
          for chromosomal conditions like Down Syndrome (Trisomy 21), Edwards 
          Syndrome (Trisomy 18) and Patau Syndrome (Trisomy 13).
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="showNuchalDialog = false">
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <!-- Fetal Weight Dialog  -->
     <v-dialog v-model="showFetalWeightDialog" max-width="500" z-index="1000" persistent>
      <v-card>
        <v-card-title class="headline">
          <v-icon left color="info">mdi-ruler</v-icon>
          Fetal Weight
        </v-card-title>

        <v-card-text class="pt-4 fetal-weight-dialog-text">
          Doctors estimates by measuring the following: 
          <ul>
            <li>Length of the main thigh bone (the femur),</li>
            <li>The distance from the top of the head to the bottom of the spine (crown-rump length),</li>
            <li>The circumferences of the head and abdomen.</li>
          </ul>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="showFetalWeightDialog = false">
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    
  </div>
</template>

<script>
export default {
  name: "UltrasoundWhatIsFetalDevelopment",

  data() {
    return {
      showEctopicDialog: false,
      showNuchalDialog: false,
      showFetalWeightDialog: false,
    };
  },

  methods: {
    getImagePath(imagePath) {
      const basePath = this.$config.basePath || (
        process.env.DEPLOY_ENV === 'GH_PAGES' ? '/pregnancy-app' : ''
      );

      return `${basePath}${imagePath}`;
    }
  },
};
</script>

<style scoped>
.medical-term-btn {
  text-transform: none !important;
  text-decoration: underline;
  min-width: auto !important;
  padding: 0 !important;
  height: auto !important;
  font-weight: 600;
  margin: 0;
  display: inline-flex !important;
  align-items: baseline;
  vertical-align: baseline;
  font-size: inherit !important;
  line-height: inherit !important;
  letter-spacing: normal !important;
  border-radius: 0 !important;
  white-space: normal;
}

.medical-term-btn .v-btn__content {
  display: inline !important;
  padding: 0 !important;
}

.medical-term-btn:hover {
  background-color: rgba(25, 118, 210, 0.04) !important;
  text-decoration: none;
}

.medical-term-btn::before {
  display: none !important;
}

/* Dialog Styles */
.v-dialog .v-card .v-card-title {
  font-weight: 600;
  padding-bottom: 8px;
}

.v-card-text p {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 0;
}

.fetal-weight-dialog-text ul {
  list-style-type: disc;
  list-style-position: outside;
  padding-left: 1.5rem;
}

.fetal-weight-dialog-text li {
  display: list-item;
  margin-bottom: 0.5rem;
}

.figure-group {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  text-align: center;
}

.subfigure {
  flex: 1 1 300px;
  margin: 0;
}

.subfigure img {
  width: 100% !important;
  max-width: 700px;
  margin: 20px auto;
  display: block;
}

.figure-group > figcaption {
  flex-basis: 100%;
}

</style>