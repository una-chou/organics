<template>
  <div class="part-footer">
    <div class="footer-tops"></div>
    <div class="footer-navs">
      <p :class="{'active': currentTab==='Company'}" @click="jumpTo('Company')">Company</p>
      <p :class="{'active': currentTab==='Products'}" @click="jumpTo('Products')">Products</p>
      <p :class="{'active': currentTab==='Laboratory'}" @click="jumpTo('Laboratory')">Laboratory</p>
      <p :class="{'active': currentTab==='Manufacturing'}" @click="jumpTo('Manufacturing')">Manufacture</p>
      <p :class="{'active': currentTab==='Contact'}">Contact us</p>
    </div>
    <div class="footer-contact footer-contact-new" style="border-top: 1px solid rgba(255,255,255,.5);">
      <div class="footer-contact-left">
        <img src="@/assets/images/logo.png" alt="">
        <p>Science-Based <br />Dietary Nutrition</p>
      </div>
      <div class="footer-sep"></div>
      <div class="footer-contact-center">
        <img src="@/assets/images/amazon.png" alt="">
        <p>Available on <br />Amazon.com</p>
      </div>
      <div class="footer-sep footer-sep1"></div>
      <div class="footer-contact-right">
        <a href="https://x.com/MissionHillFood" target="_blank" style="height:38px"><img src="@/assets/images/footer/twitter.svg" alt=""></a>
        <a href="https://www.tiktok.com" target="_blank"><img src="@/assets/images/footer/tiktok.svg" alt=""></a>
        <a href="https://www.facebook.com/profile.php?id=61560898864102" target="_blank"><img src="@/assets/images/footer/facebook.svg" alt=""></a>
        <a href="https://www.instagram.com/missionhillfoods?igsh=eXR4aHBteGp1eWs0&utm_source=qr" target="_blank" style="height:40px"><img src="@/assets/images/footer/photo.svg" alt=""></a>
      </div>
    </div>
    <div class="footer-contact footer-contact-address footer-contact-address-pc">
      <div class="footer-contact-address-left">
        <p>Business<br />Address:</p>
      </div>
      <div class="footer-sep"></div>
      <div class="footer-address-info"><p>Headquarter<br />Mission Hill Foods Inc<br />17870 Castleton ST STE 302  <br />City of Industry CA 91748, USA</p></div>
      <div class="footer-sep"></div>
      <div class="footer-address-info"><p>Canada Office<br />Mission Hill Foods Co. Ltd.<br />202-15388 24 Ave Surrey <br />BC V4A2J2 CANADA</p></div>
      <div class="footer-sep"></div>
      <div class="footer-address-info" style="justify-content: flex-end;"><p>New York Office<br />CBD Calm Inc. <br />8321 3FL Broadway, Elmhurst, <br />NY 11373 USA</p></div>
    </div>
    <div class="footer-contact footer-contact-address footer-contact-address-m">
      <div class="footer-address-title"><p>Business Address:</p></div>
      <div class="footer-address-info"><p>Headquarter: Mission Hill Foods Inc <br />17870 Castleton ST STE 302   City of Industry CA 91748, USA</p></div>
      <div class="footer-address-info"><p>Canada Office: Mission Hill Foods Co. Ltd. <br />202-15388 24 Ave Surrey  BC V4A2J2 CANADA</p></div>
      <div class="footer-address-info"><p>New York Office: CBD Calm Inc.  <br />8321 3FL Broadway, Elmhurst,  NY 11373 USA</p></div>
    </div>
    <div class="footer-contact footer-contact-email">
      <div class="footer-email-info">
        <div>Welcome to contact us at: sales@misisonhillfoods.com</div>
        <div class="footer-email-info-pc">Connect with us on Instagram, X.com, and Facebook to stay updated on all our latest news and promotions!</div>
        <div class="footer-email-info-m">Connect with us on Instagram, X.com, and Facebook to <br /> stay updated on all our latest news and promotions!</div>
        <div>Welcome to explore our products on Amazon and TikTok!</div>
      </div>
      <div class="footer-email">
        <a href="mailto:sales@misisonhillfoods.com"><img src="@/assets/images/footer/email.svg" alt=""></a>
      </div>
    </div>

    <div class="footer-icons">
      <a href="https://x.com/MissionHillFood" target="_blank" style="height:18px"><img src="@/assets/images/footer/twitter.svg" alt=""></a>
      <a href="https://www.tiktok.com" target="_blank"><img src="@/assets/images/footer/tiktok.svg" alt=""></a>
      <a href="https://www.facebook.com/profile.php?id=61560898864102" target="_blank"><img src="@/assets/images/footer/facebook.svg" alt=""></a>
      <a href="https://www.instagram.com/missionhillfoods?igsh=eXR4aHBteGp1eWs0&utm_source=qr" target="_blank" style="height:20px"><img src="@/assets/images/footer/photo.svg" alt=""></a>
    </div>
    <div class="footer-copyright">Copyright © 2024 Mission Hill Foods. All Rights Reserved</div>
  </div>
</template>
<script>
export default {
    components: {},
    props: {},
    data() {
        return {
          currentTab: '',
        }
    },
    watch: {
      '$route.name': {
        handler(newVal, oldVal) {
          console.log(newVal, oldVal);
          if (newVal) {
            this.currentTab = newVal
          }
        },
        deep: true,
        immediate: true
      }
    },
    created() {},
    mounted() {},
    methods: {
      jumpTo(name){
        this.$router.push({name:name})
      }
    }
}
</script>
<style lang='scss' scoped>
$green: #0BAB50;
$greenText: #006633;
.part-footer {
  background-color: $greenText;
  position: relative;
  padding: 0 70px;
  margin-top: 70px;
  font-weight: 500;
  .footer-tops {
    position: absolute;
    top: -17px;
    left: 0;
    width: 100%;
    height: 40px;
    background: url('./../assets/images/wave.png') repeat;
    background-size: 40px auto;
  }
  .footer-navs {
    display: flex;
    padding-top: 50px;
    padding-bottom: 50px;
    justify-content: center;
    color: #fff;
    p {
      padding: 0 20px;
      cursor: pointer;
      &:hover {
        // font-weight: bold;
        color: $green;
      }
    }
    .active {
      font-weight: bold;
    }
  }
  .footer-contact {
    width: 100%;
    border-bottom: 1px solid rgba(255,255,255,.5);
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 130px;
  }
  .footer-contact-new {
    color: #fff;
    padding: 30px 0;
    font-size: 18px;
    align-items: center;
    &>div {
      display: flex;
      align-items: center;
      // width: 33%;
      flex-shrink: 0;
    }
    .footer-contact-left {
      justify-content: flex-start;
      img {
        height: 70px;
        margin-right: 20px;
        position: relative;
        top: -5px;
      }
    }
    .footer-contact-center {
      justify-content: center;
      img {
        height: 54px;
        margin-right: 20px;
        position: relative;
        top: 10px;
      }
    }
    .footer-contact-right {
      justify-content: flex-end;
      a {
        height: 42px;
        margin-left: 20px;
        img {
          height: 100%;
          margin: 0;
        }
      }
      
    }
    .footer-sep {
      height: 70px;
      width: 1px;
      background-color: rgba(255,255,255,.5);
    }
  }
  .footer-contact-address {
    display: flex;
    align-items: center;
    padding: 30px 0;
    color: #fff;
    .footer-contact-address-left {
      font-size: 18px;
      font-weight: bold;
      // padding-right: 60px;
      flex-shrink: 0;
    }
    // .footer-contact-address-right {
      // flex: auto;
      // display: flex;
      // align-self: center;
      .footer-address-info {
        // width: 33%;
        flex-shrink: 0;
        font-size: 14px;
        display: flex;
        align-items: flex-start;
        justify-content: center;
      }
    // }
    .footer-sep {
      height: 70px;
      width: 1px;
      background-color: rgba(255,255,255,.5);
    }
  }
  .footer-contact-address-pc {
    display: flex;
  }
  .footer-contact-address-m {
    display: none;
  }
  .footer-contact-email {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 30px 0;
    color: #fff;
    // font-weight: 300;
    font-size: 15px;
    .footer-email-info {
      flex: auto;
      line-height: 1.5;
      .footer-email-info-pc {
        display: block;
      }
      .footer-email-info-m {
        display: none;
      }
    }
    .footer-email {
      height: 30px;
      flex-shrink: 0;
    }
  }
  .footer-copyright {
    text-align: center;
    padding: 50px 0 40px;
    color: #fff;
  }
  .footer-icons {
    display: none;
  }
}

@media only screen and (max-width: 1200px) {
.part-footer {
  
  .footer-contact-new {
    
    .footer-contact-left {
      img {
        height: 56px;
        margin-right: 10px;
      }
    }
    .footer-contact-center {
      img {
        height: 48px;
        margin-right: 10px;
      }
    }
    .footer-contact-right {
      a {
        height: 38px;
        margin-left: 10px;
      }
    }
  }
}
}
@media only screen and (max-width: 900px) {
.part-footer {
  padding: 0 20px;
  margin-top: 30px;
  .footer-tops {
    height: 16px;
    top: -11px;
    background-size: 26px auto;
  }
  .footer-navs {
    padding-top: 20px;
    padding-bottom: 20px;
    justify-content: space-between;
    p {
      padding: 0 5px;
      font-size: 11px;
      &:hover {
        color: #fff;
      }
    }
  }
  .footer-contact {
    height: 80px;
  }
  .footer-contact-new {
    padding: 20px 0;
    font-size: 12px;
    .footer-contact-left {
      img {
        height: 28px;
        margin-right: 10px;
        top: -1px;
      }
    }
    .footer-contact-center {
      justify-content: center;
      img {
        height: 22px;
        margin-right: 10px;
        position: relative;
        top: 5px;
      }
    }
    .footer-contact-right {
      display: none;
    }
    .footer-sep {
      height: 50px;
    }
    .footer-sep1 {
      display: none;
    }
  }
  .footer-contact-address {
    padding: 10px 0 10px;
    .footer-contact-address-left {
      font-size: 10px;
    }
    .footer-address-info {
      flex-shrink: 0;
      font-size: 10px;
      display: flex;
      align-items: flex-start;
      justify-content: center;
    }
    .footer-sep {
      display: none;
    }
  }
  .footer-contact-address-pc {
    display: none;
  }
  .footer-contact-address-m {
    display: block;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    height: max-content;
    justify-content: center;
    .footer-address-title {
      font-size: 12px;
      font-weight: 600;
      margin-bottom: 5px;
      width: 100%;
      text-align: center;
      margin-top: 5px;
    }
    .footer-address-info {
      margin-bottom: 5px;
      width: 100%;
      text-align: center;
      line-height: 1.6;
    }
  }
  .footer-contact-email {
    padding: 20px 0;
    font-size: 10px;
    .footer-email-info {
      flex: auto;
      line-height: 1.3;
      .footer-email-info-pc {
        display: none;
      }
      .footer-email-info-m {
        display: block;
      }
    }
    .footer-email {
      height: 20px;
      &>a {
        height: 100%;
        &>img {
          height: 100%;
        }
      }
    }
  }
  .footer-copyright {
    text-align: center;
    padding: 18px 0 20px;
    color: #fff;
    font-size: 12px;
  }
  .footer-icons {
    display: flex;
    align-items: center;
    width: 100%;
    justify-content: center;
    margin-top: 20px;
    a {
      height: 20px;
      margin-left: 20px;
      img {
        height: 100%;
        margin: 0;
      }
    }
  }
}
}
</style>