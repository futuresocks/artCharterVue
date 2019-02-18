<template lang="html">
  <div>
    <mapView :murals="murals"/>
  </div>
</template>

<script>
import MapView from "./components/MapView.vue";
import { eventBus } from './main.js';

export default {
  data(){
    return {
      selectedMural: null,
      murals: [{
        id: 3,
        title: "St. Mungo",
        artist: "SMUG",
        artistWebsite: "https://www.facebook.com/smuggraffiti/",
        about: "Another addition by Smug to his growing portfolio of work, this mural was completed in February 2016. Although officially untitled, it acquired its name during a period of massive social media interest when an image of this installation was shared approximately 1.5 million times within the first week.",
        nearby: "High Street is the historic heart of Glasgow. From here is easy access to Glasgow Cathedral, St Mungo Museum of Religious Life and Art, and Provand’s Lordship – Glasgow’s oldest building. Close by is Glasgow City Chambers.",
        coords: [55.860910, -4.238229],
        imageTags: "stmungo+smug",
        checked: false
      },
      {
        id: 4,
        title: "Fellow Glasgow Residents",
        artist: "SMUG",
        artistWebsite: "https://www.facebook.com/smuggraffiti/",
        about: "Before the gable end wall overlooking Ingram Street car park featured peeling paint and graffiti. Now thanks to the imagination of Smug it shows all types of animals found in Glasgow’s parks and green space appearing through what looks like holes in the wall.",
        nearby: "The Fellow Glasgow Residents Mural is in the heart of Glasgow’s popular Merchant City where there is plenty to do for all including a huge variety of restaurants and a Craft and Design Fair each Sunday 12-6pm in Merchant Square. ",
        coords: [55.859113, -4.244563],
        imageTags: "fellow+glasgow+residents+mural",
        checked: false
      },

      {
        id: 5,
        title: "Badminton",
        artist: "Guido Van Helten",
        artistWebsite: "http://www.guidovanhelten.com/",
        about: "Installed as part of the promotional campaign for 2014 Commonwealth Games, this mural is part of a series depicting various sports. Completed by the same artist, the other murals were installed adjacent to Partick Train Station and represent hockey, netball and rugby. The Badminton mural includes action shots of Scotland player Kieran Merrilees and conveys the speed of the game, as well as the athleticism required to succeed in such a competitive sport.",
        nearby: "In the heart of Glasgow’s popular Merchant City where there is plenty to do for all including a huge variety of restaurants and a Craft and Design Fair each Sunday 12-6pm in Merchant Square.",
        coords: [55.858484, -4.246589],
        imageTags: "badminton+mural+guido",
        checked: false
      },
      {
        id: 6,
        title: "Space Man",
        artist: "ReCoat",
        artistWebsite: "http://www.recoatdesign.com/",
        about: "This installation by Recoat and Ali Wylie brings colour to a city centre lane. It has been informed by Pop, graphic novels, graphic design, and Japanese culture which you can see in the slick clean lines, colour choice and geometric patterned backgrounds",
        nearby: "Close by is The Tron, with its distinctive steeple and clock, one of Scotland’s leading mid-scale producing and presenting theatres, set in the heart of Glasgow’s Merchant City. Trongate 103, which houses galleries, workshops, artist studios and production spaces. Also nearby is Tolbooth Clock Tower; all that remains of the original City Chambers, which was destroyed by fire in 1926.",
        coords: [55.857281, -4.247002],
        imageTags: "space+man+mural+recoat",
        checked: false
      },
      {
        id: 7,
        title: "Billy Connolly",
        artist: "John Byrne | Rogue-One",
        artistWebsite: "https://artuk.org/discover/artists/byrne-john-b-1940",
        about: "In commemoration of Billy Connolly’s 75th birthday BBC Scotland commissioned three portraits of the comedian by top Scottish artists. In conjunction with Glasgow City Council representations of these original works were then installed around the city centre. Two of these works have been depicted as murals by Rogue One. This particular installation is based on John Byrne’s “Billy Connolly”. All three portraits were showcased, across the country, in a special BBC Scotland programme Billy Connolly: Portrait of a Lifetime and are now on display in the People’s Palace.",
        nearby: "To the immediate West is the Style Mile’s St Enoch Centre which welcomes over 19 million shoppers each year. Just to the East are the independent retailers around Kings Court and Parnie Street. To the North is the Merchant City area of Glasgow city centre. To the North-East is High Street and the historical heart of Glasgow.",
        coords: [55.856352, -4.248621],
        imageTags: "billy+connolly+osborne+street",
        checked: false
      },
      {
        id: 8,
        title: "Study of a Woman in Black",
        artist: "James Klinge",
        artistWebsite: "http://jamesklinge.tumblr.com/",
        about: "Now working under his own name, James Klinge (aka “Klingatron”) continues his collaboration with Art Pistol whilst demonstrating the same attention to detail through his distinctive use of intricate stencil technique. However, the artist has chosen to progress his subject matter towards portraiture, a trend which has been showcased in a number of exhibitions around the world. ",
        nearby: "To the West is the Briggait; a Victorian fish-market since converted and now used as an artists’ studio and event space. To the North is the Tolbooth Clock Tower; all that remains of the original City Chambers, which was destroyed by fire in 1926. To the North-West are the independent retailers of Kings Court and Parnie Street. To the east is St Andrews in the Square, dating back to 1754 and described as one of the top six classical churches in the UK. Adjacent to the South-East is Glasgow Green, the oldest of the city’s parks having been established by Royal Grant in the 15th century. ",
        coords: [55.854816, -4.245965],
        imageTags: "studyofawomaninblack",
        checked: false
      },
      {
        id: 9,
        title: "The Clutha",
        artist: "EJEK | Rogue-One",
        artistWebsite: "https://www.facebook.com/EJEK-645912252138303/",
        about: "Rogue-One, Art Pistol and Ejek have skilfully combined to create a mural which pays homage to the history of the area, as well as celebrating a variety of personalities who visited this iconic location, famous for its atmosphere and live music. The landlord, Alan Crossan, said: The mural installed at the Clutha Bar in Glasgow has created worldwide interest and is fast becoming a tourist attraction. It will without doubt enhance the local area, brightening up an otherwise derelict building.”",
        nearby: "Just around the corner is The Briggait – a Victorian fishmarket since converted and now used as an artists’ studio and event space. Adjacent is the Style Mile’s St Enoch Centre which welcomes over 19 million shoppers each year. St Andrew’s Cathedral, built in 1816, can be seen in a new light since its restoration, completed in April 2011. ",
        coords: [55.854496, -4.250014],
        imageTags: "cluthavaults+mural+rogueone",
        checked: false
      },
      {
        id: 10,
        title: "Glasgow’s Tiger",
        artist: "Klingatron",
        artistWebsite: "http://jamesklinge.tumblr.com/",
        about: "Klingatron has collaborated with Art Pistol to re-imagine the original tiger design previously installed at this location. Incorporating a high level of detail, and occupying the same high profile location adjacent to South Portland Suspension Bridge, this mural is becoming as iconic as its predecessor.",
        nearby: "Adjacent to the Clyde Walkway at the Broomielaw this route provides access to some of Glasgow’s most recognisable sites, including the SECC, Hydro, the Clyde Auditorium and the Finnieston Crane. It offers access to Central Station and links with key cycle paths in the east, west and south of Glasgow.",
        coords: [55.855605, -4.255537],
        imageTags: "glasgowstiger",
        checked: false
      }]
    }
  },
  components: {
    'mapView': MapView
  },
  mounted(){
      //fetch mural data
      eventBus.$on('marker-clicked', index => this.selectedMural = this.murals[index])
  }
}
</script>

<style lang="css" scoped>
</style>
