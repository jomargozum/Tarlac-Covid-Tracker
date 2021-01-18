<template>
  <!--  eslint-disable vue/attribute-hyphenation  -->
  <div>
    <div class="columns" style="padding:10px;">
      <covidNumber
        v-for="covidData in covidDatas"
        :id="covidData.id"
        :key="covidData.id"
        :title="covidData.title"
        :number="covidData.number"
        :lastUpdated="covidData.lastUpdated"
      />
    </div>
    <div class="columns" style="padding:10px;">
      <div class="column is-two-thirds" style="background-color:white;">
        <div class="columns">
          <!-- //gmap -->
          <googlemap />
          <div class="column is-half" style="background-color:white;">
            <h5 class="affectedArea has-text-centered">
              Affected Areas
            </h5>
            <div class="columns is-multiline">
              <affectedArea
                v-for="areaData in areaDatas"
                :id="areaData.id"
                :key="areaData.id"
                :area="areaData.area"
                :cases="areaData.cases"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <section class="section" style="background-color:white;">
      <!-- number of deaths -->
      <numberOfDeath
        v-for="numData in numDatas"
        :id="numData.id"
        :key="numData.id"
        :num="numData.num"
      />
      <div class="columns" style="padding:10px;">
        <covidDeath
          v-for="covidDeathsData in covidDeathsDatas"
          :id="covidDeathsData.id"
          :key="covidDeathsData.id"
          :title="covidDeathsData.title"
          :cases="covidDeathsData.cases"
          :lastUpdated="covidDeathsData.lastUpdated"
        />
      </div>
    </section>
    <hotlines />
  </div>
</template>
<script>
import covidNumber from '~/components/covidNumber'
import covidDeath from '~/components/covidDeath'
import hotlines from '~/components/hotlines'
import googlemap from '~/components/gmap'
import affectedArea from '~/components/affectedArea'
import numberOfDeath from '~/components/NumberOfDeaths'
export default {
  components: {
    covidNumber,
    covidDeath,
    hotlines,
    googlemap,
    affectedArea,
    numberOfDeath
  },
  async asyncData (context) {
    // //Covid Number//
    const productResponse = await context.app.$storyapi.get('cdn/stories/', {
      version: context.isDev ? 'draft' : 'published',
      starts_with: 'covidtracker'
    })
    const covidData = productResponse.data
    // eslint-disable-next-line no-console
    const covidDatas = covidData.stories.map((bp) => {
      return {
        id: bp.slug,
        title: bp.content.title,
        number: bp.content.affectedNumber,
        lastUpdated: bp.content.lastUpdate
      }
    })
    // AFFECTED AREA //
    const area = await context.app.$storyapi.get('cdn/stories/', {
      version: context.isDev ? 'draft' : 'published',
      starts_with: 'affectedareas'
    })
    const areaData = area.data
    // eslint-disable-next-line no-console
    const areaDatas = areaData.stories.map((bp) => {
      return {
        id: bp.slug,
        area: bp.content.area,
        cases: bp.content.cases
      }
    })
    // Number of Death //
    const numDeath = await context.app.$storyapi.get('cdn/stories/', {
      version: context.isDev ? 'draft' : 'published',
      starts_with: 'numberofdeaths'
    })
    const numData = numDeath.data
    // eslint-disable-next-line no-console
    const numDatas = numData.stories.map((bp) => {
      return {
        id: bp.slug,
        num: bp.content.number
      }
    })
    // COVID DEATHs //
    const covidDeaths = await context.app.$storyapi.get('cdn/stories/', {
      version: context.isDev ? 'draft' : 'published',
      starts_with: 'coviddeaths'
    })
    const covidDeathsData = covidDeaths.data
    // eslint-disable-next-line no-console
    const covidDeathsDatas = covidDeathsData.stories.map((bp) => {
      return {
        id: bp.slug,
        title: bp.content.title,
        cases: bp.content.deathsNumber,
        lastUpdated: bp.content.lastUpdated
      }
    })
    return {
      covidDatas,
      areaDatas,
      numDatas,
      covidDeathsDatas
    }
  },
  mounted () {
    this.$storybridge.on(['unpublished', 'published', 'change'], (event) => {
      // eslint-disable-next-line eqeqeq
      if (event.action == 'unpublished') {
        window.location.reload()
      // eslint-disable-next-line brace-style
      }
      // eslint-disable-next-line eqeqeq
      else if (event.action == 'published') {
        window.location.reload()
      } else {
        window.location.reload()
      }
    })
  },
  head () {
    return {
      title: 'Tarlac Covid Tracker'
    }
  }
}
</script>
<style scoped>
.affectedArea {
    font: bold 20px sans-serif;
    color: #FF4470;
}
</style>
