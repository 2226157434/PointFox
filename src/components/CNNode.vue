<template>
  <div id="cnnodeWrapper">
    <div>
      <span>cnnode论坛</span>
    </div>
    <div>
      <li v-for="(value, index2) in this.topicsArr" :key="index2">
        {{ value.title }}
        <span>
          <img id="avatar" :src="value.author.avatar_url" >
      </span>

      </li>
    </div>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  data() {
    return {
      topicsArr: [],
    };
  },
  beforeCreated() {
    // console.log("this is before")
  },
  created() {
    let that = this;
    // console.log("this is vue")
    Axios.get("https://cnodejs.org/api/v1/topics").then(function (response) {
    //   console.log(response);
      that.topicsArr = response.data;
      if (response.data.success) {
        that.topicsArr = response.data.data;
      }
    });
  },
};
</script>

<style scoped>
#avatar {
  width: 20px;
  height: 20px;
}
</style>