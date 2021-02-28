<template>
  <div class="search-uni">
    <input type="text" placeholder='Enter Country' v-model="country">
    <input type="button" value="Find" @click="contentShow=true;" >
    <input type="button" value="Remove" @click="removeInput" >


    <div class="wrap" v-if="contentShow">
      <h1>University</h1>
      <h3 class="uni_num">#</h3>
      <h3 class="uni_code">Code</h3>
      <h3 class="uni_country">Country</h3>
      <h3 class="uni_name">Name</h3>
      <h3 class="uni_domain">Domain</h3>
      <h3 class="uni_page">Web Pages</h3>
     <div v-for="uni in university" :key="uni.id" class="uni_list" >
       <div class="uni_num"><p >{{university.indexOf(uni)+1}}</p></div>
       <div class="uni_code"> <p >{{uni.alpha_two_code}}</p></div>
       <div class="uni_country"><p >{{uni.country}}</p></div>
       <div class="uni_name"><p >{{uni.name}}</p></div>
       <div class="uni_domain"><p v-for="domain in uni.domains" :key="domain.id" >{{domain}}</p></div>
       <div class="uni_page"><a  v-for="page in uni.web_pages" :key="page.id" style="margin:1rem" :href="page">{{page}}</a></div>






     </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'


export default {
  name: 'SearchUniversity',
  props: {

  },
  data() {
    return {
      country: '',
      university: [],
      find: [],
      contentShow: false,
    }
  },
  watch: {
    country(){
      this.GetUniversity();

    }
  },
  methods: {
    GetUniversity(){
      axios
          .get('http://universities.hipolabs.com/search?country='+this.country)
          .then(response => (this.university = response.data));

    },
    removeInput(){
      this.contentShow=false;
      this.country='';
    }
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

input {
  margin: 10px;
  border-radius: 10px;
  outline: none;
  padding: 3px;
}
input[type=button]{
  background-color: #2c3e50;
  color: #FFFFFF;
  width: 75px;
}
.wrap {
  display: flex;
  width: 80%;
  justify-content: left;
  flex-wrap: wrap;
  margin: 0 auto;


}
.wrap h1 {
  flex-basis: 100%;
}
.uni_list {
  display: flex;
  width: 100%;
  justify-content: start;


}
h3 {
  border: 1px solid grey;
  margin-top: 16px;
  font-size: 13px;
}
.uni_list   div{
  border: 1px solid grey;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding: 3px;
  font-size: 12px;
}

.uni_num {
  flex-basis: 3%;
}
.uni_code {
  flex-basis: 5%;
}
.uni_country {
  flex-basis:13%;
}
.uni_name {
  flex-basis: 34%;
}
.uni_domain {
  flex-basis: 15%;
}
.uni_page {
  flex-basis: 30%;
  border: 1px solid grey;

}
 a {
  width: 100%;
  margin: 0;

}
</style>
