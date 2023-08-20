<template>
  <div id="container">
    <div>
      <div class="desc-container">
        <h1>Edit: <em><div contentEditable="true">{{ article.title }}</div></em></h1>
        <hr class="hr-dotted">
        <br>
        <p class="editable description" contentEditable="true" v-html="article.description" />
        <br>
      </div>
      <div class="img-container">
        <div class="colored-bg">
          <div style="height: 80px">
            <div class="elder-certified"><img src="/image/elder-certified.png" alt="Elder Certified" style="height: 20px" /> Elder Certified</div>
            <button class="return-button" type="button">
              <nuxt-link :to="`/article/${article.id}`">Return to Article</nuxt-link>
            </button>
          </div>
          <img class="big-image" :src="`/image/sites/${article.image}`" :alt="`Image of ${article.id}`" />
        </div>
      </div>
    </div>
    <div v-if="article.audio" style="clear: both; padding-top: 20px">
      <hr class="hr-solid">
      <h2>Voice Recording</h2>
      <audio controls :src="`/audio/sites/${article.audio}`">
        <a :href="`/audio/sites/${article.audio}`">Download audio</a>
      </audio>
      <div class="transcript-text">
        <br>
        <u>Transcript:</u>
      </div>
      <br>
      <p class="editable description" contentEditable="true" v-html="article.audio_transcript" />
    </div>
  </div>
</template>
  
<script>
export default {
  async asyncData({ params }) {
    // This is a simple representation. In a real-world scenario, you'd fetch the article data from an API or database.
    const articles = {
      '1': {
        id: '1',
        title: 'Montague Island / Gulaga',
        description: `The Indigenous history of Montague island is told by the dreamtime story of Gulaga, the revered mountain considered the maternal figure and sacred landmark by some Indigenous clans. The narrative unfolds around her two sons, Barranguba and Najanuga.<br><br>Barranguba symbolises Montague Island, known by that name among non-Indigenous people. He is the elder son of Gulaga. According to the story, Gulaga had two sons, Barranguba and Najanuga, with Barranguba being the eldest.`,
        image: 'montague-island.jpg',
        audio: 'gulaga-story.mp3',
        audio_transcript: `Gulaga Mountain is the Mother Mountain. She has two sons, Najanuga and Baranguba. Baranguba is the older son. Najanuga is the baby son.  She is also pregnant. She lies down on her side. Her head is south and her feet face north — and she is facing out to sea.<br><br>And the story goes that one day her and her two sons, were walking east to collect bush tucker. The oldest son Baranguba asked if he could go fishing and she said, 'No, you're too young, you're to stay next to me'.<br><br>As they walked along, Baranguba was insistent that he go fishing and get some fish for dinner. But she said, 'No, no, you have to stay next to me, it's not safe to go fishing by yourself'. But Baranguba snuck away. He made himself a canoe and he rowed out to sea, and a big wave came and washed him off the canoe and then he laid down in the water — and that's where he still lives today.<br><br>And when the younger son had seen this, he wanted to move away and set up his own camp. She said, 'No, you're too young, you just sit here right next to me'. So now she lies down, she looks out to sea at her older son, and baby son is right next to her, in arm's reach or her.`
      },
      '2': {
        id: '2',
        title: 'Koonadan',
        description: `The Koonadan Historic Site, located 9 km northwest of Leeton, New South Wales, holds significance as a Wiradjuri ceremonial and burial grounds. Designated as an Aboriginal Place, it features a picnic shelter with informative signs adorned with local Aboriginal artwork. Before European colonisation, the Koonadan lunette dune served as a vital hunting and fishing ground for the Wiradjuri people, positioned adjacent to Tuckerbil Swamp. A bora ground once existed in the area but has been erased due to changing land use. In the late 19th century, the Wiradjuri population was relocated to other places, eventually returning in the mid-20th century due to the closure of missions and reserves. Subsequent land alterations, including tree clearance and draining Tuckerbil Swamp, have impacted the area's resources.<br><br>During the early 1980s, sand mining at Koonadan exposed skeletal remains, prompting their reburial by the local Aboriginal community. Protests against sand mining led to its cessation, and an agreement between the landholder and the NSW government resulted in the purchase of the southern part of the Koonadan dune. This section was subsequently designated an 'Aboriginal place' under the NSW National Parks and Wildlife Act.`,
        image: 'koonadan-historic-site.jpg'
      },
      '3': {
        id: '3',
        title: 'Baerami Creek',
        description: `Baerami Creek, located in New South Wales, Australia, is a locality within the Muswellbrook Shire, situated in the Upper Hunter region. It encompasses a valley named after the watercourse, Baerami Creek. The area lies on the traditional lands of the Wonnarua people.<br><br>The locality holds significance due to its oil shale deposit, reputedly one of the largest in New South Wales, and about twice the size of the one at Glen Davis. This deposit, though referred to as 'Baerami', is situated south of the adjacent Baerami locality. Attempts to exploit the oil shale began around 1915, with substantial operations initiated in the 1920s. Various companies and mining efforts were undertaken, with the Standard Oil Company of Australia being involved, but plans were hindered by factors including government regulations and the failure of the shale oil industry at Glen Davis. Ultimately, no significant oil shale mining has occurred since 1945.<br><br>Today, remnants of the shale mine site can be found adjacent to Baerami Creek, which is now part of the Wollemi National Park. The locality once boasted a school, post office, and community hall.`,
        image: 'baerami-creek.png'
      },
      '4': {
        id: '4',
        title: 'Mungo National Park',
        description: `Mungo National Park, situated in south-western New South Wales, stands as a safeguarded sanctuary of natural beauty. Encompassing an expansive 110,967 hectares, this cherished national park lies approximately 875 kilometres west of Sydney within the Balranald Shire. Holding deep cultural significance, Mungo National Park serves as the historic convergence point for the Muthi Muthi, Nyiampaar, and Barkinji Aboriginal Nations.<br><br>As part of the UNESCO World Heritage, the national park is a pivotal piece of a 2,400 square kilometre puzzle that encompasses 17 dry lakes. The creek that once flowed into Mungo is currently preserved as a sacred site. Reverence for the past persists as the park upholds a sacred space by conserving the creek once flowing into Mungo.<br><br>Positioned around roughly 145 kilometres (about a 90-minute drive southwest of Ivanhoe), Mungo National Park beckons as a retreat. Although accessible by most vehicles along unpaved roads, it's important to be aware of potential road closures by local authorities during periods of rainy weather.<br><br>Formerly open to independent exploration, access to the sand dunes has become more regulated, compelling all visitor groups to be guided by accredited professional tour guides. This measure ensures the delicate ecosystem's preservation and respect for the land's historical value.`,
        image: 'mungo-national-park.jpg'
      },
      '5': {
        id: '5',
        title: 'Baiame Cave',
        description: 'Baiame cave is an important cultural heritage site, which features ancient cave art.',
        image: 'baiame-cave.jpg',
        audio: 'baiame-cave.mp3',
        audio_transcript: `Baiame Cave is a heritage-listed cave and cultural site of the Wanaruah, Wonnarua People.<br><br>Baiame Cave is located in the foothills of the eastern side of the Great Dividing Range in Milbrodale, on privately owned farmland, a few kilometres north of the boundary of Yengo National Park.<br><br>The artwork is visible on the rear wall of the cave and depicts a larger-than-life male figure, outlined with white pigment and filled with a red pigment, with two large white circles for eyes and both arms outstretched.`
      },
      '6': {
        id: '6',
        title: 'Mutawintji Historic Site',
        description: `If the breathtaking landscape of Mutawintji fails to leave you breathless, then the Aboriginal art adorning Mutawintji Historic Site certainly will. This remarkable region within Mutawintji National Park boasts one of the most exceptional compilations of Aboriginal art in New South Wales.<br><br>To access this extraordinary park, you must partake in a guided tour provided by Mutawintji Heritage Tours. Embark on a two to four-hour hike, unraveling the site's history and culture. The journey begins with an audio-visual presentation and continues through the ancient terrain. While certain sections of the trek leading to the site present challenges, your attention will likely be absorbed by the striking landscapes, mitigating their impact. The marvels of Mutawintji's ancient history unfold at every turn. Witness Aboriginal rock engravings and ochre stencils. Across the flat plains, you'll encounter remnants of fireplaces, stone flakes, and grinding stones.<br><br>Both children and adults will relish the opportunity to engage with Aboriginal guides as they share their Dreamtime narratives. For those seeking to extend their stay, Homestead Creek campground offers a chance to immerse in the tranquillity of the Australian outback. Delight in uninterrupted sunrises, sunsets, and the captivating brilliance of the outback's starlit sky.`,
        image: 'mutawintji-historic-site.jpg'
      }
    };

    return {
      article: articles[params.id] || {}
    };
  }
}
</script>

<style scoped>
#container {
  padding: 10px 10px 50px 10px;
  margin: 0 auto;
  align-items: center;
  text-align: center;
  color: #bfafa6;
}
.description {
  text-indent: 1.5em;
  text-align: left;
  margin: 0 10% 0 10%;
}
h1, h2 {
  margin-bottom: 10px;
  color: #603030;
}
h1 {
  margin-top: 20px;
}
hr.hr-dotted {
  border-top: 3px dotted #bfafa6;
  margin-bottom: 20px;
}
hr.hr-solid {
  border-top: 3px solid #bfafa6;
  margin-bottom: 20px;
}
img.big-image {
  border-radius: 20px;
  max-width: 95% !important;
}
.img-container {
  float: right;
  width: 60%;
  padding: 20px;
}
.desc-container {
  float: left;
  width: 40%;
}
button.return-button {
  float: right;
  border-radius: 5px;
  padding: 15px 30px;
  background-color: #cb9d9d;
}
button.edit-button > a {
  text-decoration: none !important;
  color: white !important;
}
.elder-certified {
  float: left;
  padding: 13px 13px;
  font-weight: bold;
  font-size: 20px;
  color: #efdace;
}
.colored-bg {
  padding: 10px;
  background-color: #c7c0c0;
  border-radius: 20px;
}
.transcript-text {
  font-size: 20px;
}
[contentEditable="true"] {
  background-color: #eeeeee;
  color: #3f3333;
}
</style>
