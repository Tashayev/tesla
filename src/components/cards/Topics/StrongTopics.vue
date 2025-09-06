<script setup>
import imgs1 from './../../../assets/strong-1.jpg'
import imgs2 from './../../../assets/strong-2.jpg'
import imgs3 from './../../../assets/strong-3.jpg'
import imgw1 from './../../../assets/weack-1.jpg'
import imgw2 from './../../../assets/weack-2.jpg'
import imgw3 from './../../../assets/weack-3.jpg'
import TopicCard from './TopicCard.vue'


const topicData = [
  {
    title: 'Strongest Topics',
    topics: [
      {
        name: "Covid Protocols",
        image: imgs1,
        percentage: 95

      },
      {
        name: "Cyber Security Basics",
        image: imgs2,
        percentage: 92

      },
      {
        name: "Social Media Policies",
        image: imgs3,
        percentage: 89

      },
    ]
  },
  {
    title: 'Weackest Topics',
    topics: [
      {
        name: "Food Safety",
        image: imgw1,
        percentage: 74
      },
      {
        name: "Compliance Basics Procedures",
        image: imgw2,
        percentage: 52

      },
      {
        name: "Company Networking",
        image: imgw3,
        percentage: 36
      },
    ]
  },
]

</script>

<template>
  <div v-for="(topic, index) in topicData" class="w-full">
    <TopicCard :title="topic.title" :index="index" :topics="topic.topics" />
  </div>
</template>
