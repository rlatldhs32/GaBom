<template>
  <v-card
    class="mx-auto"
    tile
  >
    <v-sheet
      class="mx-auto"
      elevation="8"
      max-width="800"
    >
      <v-img
        height="300px"
        src="../assets/images/test5.png"
      >
        <v-row
          align="end"
          class="fill-height"
        >
          <v-col
            align-self="end"
            class="pa-0"
            cols="12"
          >
            <v-row 
                justify="center">
              <v-avatar
                class="profile" 
                color="grey"
                size="128px"
              >
                <img :src="profileImage"/>
                <upload-image class="update-image"></upload-image>
              </v-avatar>
            </v-row>
          </v-col>
          <v-col class="py-0" align-self="center">
            <v-bind style="font-size: 24px"><b>{{ nickname }}</b></v-bind><br>
            <v-btn text><v-text>팔로워 <b>{{follower}}</b></v-text></v-btn>&nbsp;&nbsp;&nbsp;&nbsp; 
            <v-btn text><v-text>팔로잉 <b>{{following}}</b></v-text></v-btn><br>
            <!--<v-text>{{ introduction }}</v-text>-->
          </v-col>
        </v-row>
      </v-img>
    </v-sheet>
  </v-card>
</template>

<script>
import UploadImage from './UploadImage.vue'
export default {
    data() {
        return {
            profileImage: require('../assets/images/profile-example.jpg'),
            nickname: '존잘윤세연',
            introduction: '안녕하세요. 여행이 좋아!',
            follower: 179,
            following: 279,
        }
    },   
    methods: {
      updateImage() {
        if (!this.profileImage) {this.url="No File"}
        let reader = new FileReader();
        reader.readAsDataURL(this.profileImage);
        reader.onload = () => {
          this.url = reader.result;
        }
      },
    },
    components:{
        UploadImage
    }     
}
</script>

<style>
.profile {
  position: relative;
}
.update-image {
  position: absolute;
}
</style>