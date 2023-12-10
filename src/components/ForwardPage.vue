<template>
  <div>
    <!-- Button to open the pop-up -->
    <button @click="showPopup = true" class="pop-upButton">Open Pop-up</button>

    <!-- Pop-up container that appears when showPopup is true -->
    <div class="container-floid" v-if="showPopup">
      <div class="pop_up">
        <!-- Title and close button section -->
        <div class="title_closebutton">
          <!-- Title of the pop-up -->
          <p class="forward_title">Forward</p>
          <!-- Close button to hide the pop-up -->
          <button type="button" class="btn-close btn-close-white" aria-label="Close" @click="showPopup = false"></button>
        </div>

        <!-- Label and search input for filtering -->
        <label class="label_title">Select one person</label>
        <svg class="fa fa-search" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"><path d="M11.5 21C16.7467 21 21 16.7467 21 11.5C21 6.25329 16.7467 2 11.5 2C6.25329 2 2 6.25329 2 11.5C2 16.7467 6.25329 21 11.5 21Z" stroke="#546076" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/><path d="M22 22L20 20" stroke="#546076" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
        <input type="text" class="form-control form-input" placeholder="Search">

        <!-- Loop through the person_info array to display individuals -->
        <div v-for="(item, index) in person_info" :key="index" class="same_line">
          <!-- Display person's image -->
          <div class="circle_pic"><img :src="item.picture_path" alt="Person's image"/></div>
          <!-- Display person's name -->
          <div class="font"><p class="name_font">{{ item.name }}</p></div>
          <!-- Radio input for person selection -->
          <label class="form-check-label">
            <input class="form-check-input-radio mb-4 me-1" type="radio" name="soundSelection"/>
            <span class="checkmark"></span>
          </label>
        </div>

        <!-- Button to proceed with forwarding action -->
        <button class="button_forward">Forward</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showPopup: false,
      person_info: [
        { picture_path: require('@/assets/images/dima.png'), name: 'Dima Shurafa' },
        { picture_path: require('@/assets/images/dima.png'), name: 'Dima Shurafa' },
        { picture_path: require('@/assets/images/dima.png'), name: 'Dima Shurafa' },
        { picture_path: require('@/assets/images/dima.png'), name: 'Dima Shurafa' }
      ]
    };
  }
};
</script>

<style scoped>
 /* Import Google Fonts for Poppins */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap");

/* Styling for the pop-up container */
.pop_up {
  box-sizing: border-box;
  width: 550px;
  height: 701px;
  margin: 100px 0px 0px 100px;
  background-color: #040D21;
  border: 2px solid;
  border-style: solid;
  display: block;
  font-style: normal;
  line-height: normal;
  font-family: Poppins;
  text-transform: capitalize;
  border-radius: 20px;}

/* Common font weight for specific elements */
.name_font, .button_forward, .forward_title, label { font-weight: 500; }

/* Styling for circle picture */
.circle_pic img {
  width: 60px;
  height: 60px;
  margin-top: 30px;}

/* Styling for person's name */
.name_font {
  color: var(--fafafa, #FAFAFA);
  font-size: 16px;
  margin: 50px 0 0 17px;
  width: 130px;}

/* Flex layout for same line elements */
.same_line {
  display: flex;
  width: 490px;
  height: 90px;
  margin-left: 30px;}

/* Styling for forward button */
.button_forward,.pop-upButton {
  border: none;
  width: 250px;
  height: 60px;
  border-radius: 10px;
  background: var(--3-ac-2-cb, #3AC2CB);
  color: var(--fafafa, #FAFAFA);
  font-size: 20px;
  margin: 45px 0 0 150px;}

/* Hover effect for cards */
.card:hover { border-color: #3AC2CB; }

/* Styling for forward title */
.forward_title {
  color: var(--fafafa, #FAFAFA);
  font-size: 20px;
  margin-left: 233px;}

/* Styling for title and close button section */
.title_closebutton {
  margin-top: 30px;
  display: flex;}

/* Styling for close button */
.btn-close { margin-left: 188px; }

/* Styling for label title */
.label_title {
  color: var(--a-4-b-4-cb, #A4B4CB);
  font-size: 14px;
  margin: 10px 0 20px 30px;}

/* Styling for search icon */
.fa-search {
  position: absolute;
  margin: 68px 0 0 -108px;
  background-color: #040D21;}

/* Styling for form input */
.form-input {
  text-indent: 39px;
  border-radius: 10px;
  border: 1px solid #546076;
  width: 490px;
  height: 60px;
  margin: 0 0 10px 30px;
  background-color: #040D21;}

/* Styling for focused form input */
.form-input:focus {
  box-shadow: none;
  border: 1px solid #3AC2CB;
  background-color: #040D21;
  color: #FAFAFA;}

/* Styling for radio input and custom checkmark */
.checkmark {
  position: relative;
  display: inline-block;
  width: 21px;
  height: 21px;
  border: 2px solid #3AC2CB;
  border-radius: 10px;
  margin: 50px 0 0 266px;}

/* Show the custom checkmark when the radio button is checked */
.form-check-input-radio:checked ~ .checkmark { background-color: #3AC2CB; }

/* Styling for inner checkmark shape */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;}

/* Show the checkmark shape when the radio button is checked */
.form-check-input-radio:checked ~ .checkmark:after {
  display: block;
  left: 7px;
  top: 3px;
  width: 5px;
  height: 10px;
  border: solid #FAFAFA;
  border-width: 0 3px 3px 0;
  transform: rotate(45deg);}

/* Hide the default radio input */
.form-check-input-radio { display: none; }

</style>
