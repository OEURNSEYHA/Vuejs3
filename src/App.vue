<script>
export default {
  name: "App",
  data() {
    return {
      name: "seyha",
      hack: `<a  href="#" onclick={alert("hello")}> Win a prize</a>`,
      headingId: "heading",
      isDisabled: false,
      status: "danger",
      isPromoted: true,
      isSoldout: false,
      highlightColor: 'orange',
      headerSize: 90,
      objectStyle: {
        fontSize: "30px",
        color: "blue",
        fontWeight: 700
      },

      objectStyles: {
        "text-decoration": "underline"
      },
      // condition
      num: 0,
      vShow: false,
      // list rendering
      names: ['Seyha', "Nona", "Linda"],
      fullName: [
        { 
          firstName: "bruce", lastName: 'Wayne'
        },
        { 
          firstName: "seyha", lastName: 'oeurn'
        }
      ],
      actors: [
        {
          name: "christian Bale",
          movies: ["Batman", "The Prestige"]
        },{
          name: 'Di Caprio',
          movies: ['Titanic', 'Inception']
        }
      ],
      myInfo: {
        name: "seyha",
        subject: "computer Science"
      }
    };
  },
};


</script>

<template>
  hello {{ name }}
  <div v-html="hack"></div>
  <h2 v-bind:id="headingId">Heading</h2>
  <p class="a" id="idhelo">hello</p>
  <button v-bind:disabled="isDisabled">Bind</button>
  <h1 class="underline">Underlined text</h1>
  <h1 v-bind:class="status" class="underline">status</h1>
  <h1 v-bind:class="isPromoted && 'promote'">Promoted Movie</h1>
  <h1 v-bind:class="isSoldout ? 'sold-out' : 'new'">Soldout Movie</h1>
  <h1 v-bind:class="[isPromoted && 'promoted', isSoldout ? 'sold-out' : 'new']">
    Array conditional movies
  </h1>
  <h2 v-bind:class="{ promoted: isPromoted, new: !isSoldout }">
    Object conditional movie
  </h2>
  <h2 v-bind:style="{color: highlightColor}" > Inline style </h2>
  <h2 v-bind:style="objectStyle">Object style</h2>
  <h2 :style=" [objectStyle, objectStyles]"> Objects Style</h2>
  <!-- condition Rendering -->

  <h2 v-if="num === 0">  The number is Zero</h2>
  <h2 v-else-if="num < 0">The number is negative</h2>
  <h2 v-else-if="num > 0">The number is positive</h2>
  <h2 v-else="num === 0">  The number Not Zero {{ num }}</h2>
  <h2 v-show="vShow"> V-Show</h2>

  <!-- list rendering -->
  <h2 v-for="(name,index ) in names" :key="name">{{ index }} {{ name }} </h2>
  <h2 v-for="(name, index) in fullName" :key="name">{{ index }}  {{ name.firstName + name.lastName }} </h2>
<div v-for="actor in actors" :key="actor.name">
<h2>{{ actor.name }}, Movies: <span v-for="movie in actor.movies" :key="movie"> {{ movie }}</span></h2></div>
<h2 v-for="(value, key, index) in myInfo" :key="value">{{ key }}  {{index}} My name is{{ value.name }}, my major {{value.subject}}</h2>
</template>

<style scoped></style>
