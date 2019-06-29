<template>
  <div class="home">
    <app-header></app-header>
    <div class="hero">
      <div class="background-image" :style="{'background-image': `url(${require('@/app/assets/img/hero.jpg')})`}"></div>
    	<form class="contact-form" @submit.prevent="onSubmit">
        <h1 class="is-heading is-orange">Contact Form</h1>
        <label class="label">Name</label>
        <div class="control">
          <input class="input" required name="name" v-model='contact.name' placeholder="Name" type="text" autocomplete="off" >
        </div>
        <label class="label">Name</label>
        <div class="control">
          <input class="input" required name="email" v-model="contact.email" placeholder="E-mail" type="email" autocomplete="off">
        </div>
        <div class="control">
          <select class="input" v-model="selected" required>
            <option value="" disabled selected>What is your reason for contacting us</option>
            <option>Feature request</option>
            <option>Other</option>
          </select>
        </div>
        <label class="label">Message</label>
        <div class="control">
          <textarea class="input" name="message" v-model="contact.message" rows="6" placeholder="Message"></textarea>
        </div>
			  
		    <button class="button is-info" >Send</button>
		  </form>  
    </div>
  </div>
</template>
<script>
import appHeader from '@/app/components/appHeader'
export default{
  data() {
    return{
      contact: {
			name: '',
			email: '',
			message: '',
		},
    selected:'',
		isSending: false
    }
	},

	methods: {
		onSubmit(submitEvent){
      window.open('mailto:milanzaric54@gmail.com?subject='+this.selected+'&body=name:'+this.contact.name+'%0D%0Aemail: '+this.contact.email+'%0D%0Amessage: '+this.contact.message)
    }
  },
  components: {
    appHeader
  }
}
</script>
<style  lang="scss" scoped>
@import '@/app/styles/index.scss';

.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  justify-content: center !important;
  min-height: 100vh;
  color: #fff;
  text-align: center;
  z-index: 0;
  .background-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-size: cover;
    background-color: #2196f3;
    z-index: -1;
    &:after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: #414a4f;
      opacity: 0.75;
    }
  }
  .contact-form{
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    width: 40%;
    background: #F9F9F9;
    padding: 25px;
    border-radius: 15px;
    .control{
      .input{
        height: auto;
        margin-bottom: 20px;
        text-indent: 5px;
      }
    }
  }
}
@media(max-width: 768px){
  .hero{
    .contact-form{
      width:60%;
    }
  }
  
}
</style>