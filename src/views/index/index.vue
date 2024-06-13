<template>
  <div class="index-container scroll-container">
    <div class="top-nav-m"><Header /></div>
    <div class="top-nav" :style="{backgroundColor: fixedMenu ? '#006633' : 'transparent'}">
      <div class="top-nav-notice">Mission Hill Foods <span style="display:inline-block;width:10px"></span> Science-Based Dietary Nutrition</div>
      <a class="logo" href="/"><img :src="require('@/assets/images/logo.png')" alt=""></a>
      <ul class="nav-list">
        <li :class="{'active': currentTab==='Company'}" @click="jumpTo('Company')">Company</li>
        <li :class="{'active': currentTab==='Products'}" @click="jumpTo('Products')">Products</li>
        <li :class="{'active': currentTab==='Laboratory'}" @click="jumpTo('Laboratory')">Laboratory</li>
        <li :class="{'active': currentTab==='Manufacturing'}" @click="jumpTo('Manufacturing')">Manufacturing</li>
        <li :class="{'active': currentTab==='Contact'}" @click="jumpTo('Contact')">Contact us</li>
      </ul>
    </div>

    <div class="part-swiper  animate__animated animate__fadeIn">
      <el-carousel :autoplay="true" arrow="never">
        <el-carousel-item>
          <div class="top-swiper" @click="jumpTo('Company')">
            <div class="top-swiper-text animate__animated animate__fadeIn animate__delay-1s">Science-Based Dietary Nutrition</div>
          </div>
        </el-carousel-item>
        <el-carousel-item>
          <div class="top-swiper top-swiper2" @click="jumpTo('Products')">
            <div class="top-swiper-text animate__animated animate__fadeIn animate__delay-4s">Over 12 Million Bottles Sold Globally Every Year</div>
          </div>
        </el-carousel-item>
        <el-carousel-item>
          <div class="top-swiper top-swiper3" @click="jumpTo('Laboratory')">
            <div class="top-swiper-text animate__animated animate__fadeIn animate__delay-4s">Our Fully Functional Nutrition Laboratory</div>
          </div>
        </el-carousel-item>
      </el-carousel>
    </div>
  <div class="screenPadding">
    <div class="part-populars" ref="PopularsRef">
      <div class="common-titles" :class="{'animate__animated animate__zoomIn': isPopularsShow}">POPULAR CATEGORIES</div>
      <div class="popular-lists">
        <div class="popular-lis" v-for="(item,index) in PopularLists.slice(0,6)" :key="index">
          <div class="popular-items" @click="$router.push({name:'Categories', query:{type:item.id}})" :class="isPopularsShow?`animate__animated animate__fadeIn animate__delay-${index<3?1:2}s`:''">
            <div class="popular-wrap">
              <img class="popular-pics" :src="item.picture" alt="">
            </div>
            <div class="popular-title">{{item.name}}</div>
            <div class="popular-textwrap"
              :style="{'background':'linear-gradient(to left, '+ item.color +' 0%, rgba(255, 255, 255, 0) 100%)'}"
            >
              <div class="hpcglItemTextInner">
                <div class="hpcglItemTitle">{{item.name}}</div>
                <div class="hpcglItemDesc">{{item.desc}}</div>
                <div class="hpcglItemBtnsWrap">
                  <a href="" class="hpcglItemBtns hpcglItemBtns_viewProducts">View Products</a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="whole-popular-lis" @click="jumpTo('Categories')" ref="WholePopularRef" :class="isPopularsShow?`animate__animated animate__fadeIn animate__delay-3s`:''">
        <div class="whole-popular-items">
          <div class="whole-popular-wrap">
            <img class="whole-popular-pics" src="@/assets/images/pop9.png" alt="">
          </div>
          <div class="whole-popular-centers" :class="isPopularsShow?`animate__animated animate__fadeIn animate__delay-4s`:''">
            <div>We offer 15 different categories of products, </div>
            <div>including our house brand and brands manufactured for our clients.</div>
          </div>
        </div>
      </div>
    </div>

    <div class="part-sellers" ref="SellersRef">
      <div class="common-titles" :class="{'animate__animated animate__zoomIn': isSellersShow}">BEST SELLERS</div>
      <div class="sellers-lists">
        <div class="sellers-li-wrap" v-for="(item, index) in SellerLists.slice(0,4)" :key="index" :class="{'animate__animated animate__zoomIn animate__delay-1s': isSellersShow}">
          <div class="sellers-items" @click="gotoView(item.unique)">
            <div class="sellers-pics">
              <img :src="item.picture" alt="">
            </div>
            <p class="sellers-titles">{{ item.name }}</p>
            <div class="sellers-descs">{{ item.desc }}</div>
            <div class="sellers-btns" >LEARN MORE</div>
          </div>
        </div>
      </div>
      <div class="view-all-wrap all-products-view" :class="{'animate__animated animate__zoomIn animate__delay-3s': isSellersShow}">
        <div class="view-all" @click="jumpTo('Products')">View All Products </div>
      </div>
    </div>

    <div class="part-introduce-pc">
      <div class="part-introduce" ref="IntroduceRef">
        <div class="introduce-title" ref="NutritionLab">Mission Hill Foods Nutrition Lab</div>
        <div class="introduce-subtitle">Vancouver, BC Canada</div>
        <div class="introduce-wrap">
          <div class="introduce-wrap-left">
            <div class="introduce-wrap-text">Since 2014, we've invested in a series of research and development activities, including studies covering nutrient relationships with aging, weight control, vision protection, gut health, metabolism, heart and cardiovascular health, and more.</div>
          </div>
          <div class="introduce-wrap-right">
            <div class="introduce-video">
              <video
                src="@/assets/video/30s.mp4"
                ref="video"
                style="width:100%;"
                controls
                muted
                autoplay
                preload="metadata"
                webkit-playsinline="true"
                playsinline="true"
                x-webkit-airplay="allow"
                x5-video-player-type="h5"
                x5-video-player-fullscreen="false"
                x5-video-orientation="landscape"
                >
                抱歉，您的浏览器不支持内嵌视频!
              </video>
            </div>
          </div>
        </div>
        <div class="introduce-wrap">
          <div class="introduce-wrap-left">
            <div class="introduce-wrap-more" @click="jumpTo('Manufacturing')">
              Learn more
            </div>
          </div>
          <div class="introduce-wrap-right">
            <div class="introduce-fullscreen" @click="goFullscreen">View full screen</div>
          </div>
        </div>
      </div>
    </div>

    <div class="part-introduce-m">
      <div class="part-introduce" ref="IntroduceRef">
        <div class="introduce-title" ref="NutritionLab">Mission Hill Foods Nutrition Lab</div>
        <div class="introduce-subtitle">Vancouver, BC Canada</div>
        <div class="introduce-wrap">
          <div class="introduce-wrap-left">
            <div class="introduce-wrap-text">Since 2014, we've invested in a series of research and development activities, including studies covering nutrient relationships with aging, weight control, vision protection, gut health, metabolism, heart and cardiovascular health, and more.</div>
          </div>
        </div>
        <div class="introduce-wrap introduce-wrap-view">
          <div class="introduce-wrap-left">
            <div class="introduce-wrap-more" @click="jumpTo('Manufacturing')">
              Learn more
            </div>
          </div>
        </div>
      </div>

      <div class="introduce-video">
        <video
          src="@/assets/video/30s.mp4"
          ref="video"
          style="width:100%;"
          controls
          muted
          autoplay
          preload="metadata"
          webkit-playsinline="true"
          playsinline="true"
          x-webkit-airplay="allow"
          x5-video-player-type="h5"
          x5-video-player-fullscreen="false"
          x5-video-orientation="landscape"
          >
          抱歉，您的浏览器不支持内嵌视频!
        </video>
      </div>
    </div>

    <div class="part-Manufacture" ref="ManufactureRef">
      <div class="manufacture-title">MANUFACTURING</div>
      <div class="manufacture-subtitle">
        Our manufacturing facilities, based in California, USA and British Columbia, Canada, 
        <br />include two manufacturing sites in: 
        <br />Richmond, BC, Canada and Chino, California, USA.
      </div>

      <div class="manufacture-content">
        <div class="manufacture-swiper-content">
          <div class="manufacture-image">
            <el-image :src="require('@/assets/images/factory1.png')" :preview-src-list="[require('@/assets/images/factory1.png'), require('@/assets/images/factory2.png')]"></el-image>
          </div>
          <div class="manufacture-name">California, USA</div>
        </div>
        <div class="manufacture-swiper-content">
          <div class="manufacture-image">
            <el-image :src="require('@/assets/images/factory2.png')" :preview-src-list="[require('@/assets/images/factory1.png'), require('@/assets/images/factory2.png')]"></el-image>
          </div>
          <div class="manufacture-name">British Columbia, Canada</div>
        </div>
      </div>

      <div class="view-all-wrap view-all-Manufacturing" style="">
        <div class="view-all" @click="jumpTo('Manufacturing')">View All </div>
      </div>
    
    </div>
  </div>

  <Footer />

  </div>
</template>
<script>
import {PopularLists, SellerLists} from '@/products.js'
import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue'

export default {
  components: { Footer,Header },
  props: {},
  data() {
    return {
      PopularLists,
      SellerLists,
      fixedMenu: false,
      currentTab: '',
      observer: null,

      scrollT: '',
      stopscroll: '',
      currentScroll: 0,

      isPopularsShow: false,
      isSellersShow: false,
      isIntroduceShow: false,
      isManufactureShow: false,
      isFooterShow: false,
    }
  },
  created() {
  },
  mounted() {
    window.addEventListener('scroll', () => {
      let scrollTop = document.documentElement.scrollTop || document.body.scrollTop
      this.fixedMenu = scrollTop > 10
      this.handleScroll()
    })
  },
  methods: {
    goFullscreen() {
      var video = this.$refs.video;
      if (video.requestFullscreen) {
        video.requestFullscreen().catch(() => {});
      } else if (video.mozRequestFullScreen) { /* Firefox */
        video.mozRequestFullScreen();
      } else if (video.webkitRequestFullscreen) { /* Chrome, Safari & Opera */
        video.webkitRequestFullscreen().catch(() => {});
      } else if (video.msRequestFullscreen) { /* IE/Edge */
        video.msRequestFullscreen();
      }
    },
    jumpTo(name){
      if (name == 'Contact') {
        this.$nextTick(() => {
          let scrollEl = document.querySelector('.scroll-container');
          if (scrollEl) window.scrollTo({ top: scrollEl.clientHeight, behavior: 'smooth' });
        });
      } else {
        this.$router.push({name:name})
      }
    },
    gotoView(value) {
      this.$router.push({name:'Details', query: {unique: value}})
    },
    handleScroll() {
      this.currentScroll = window.pageYOffset
      let height = document.documentElement.clientHeight - 100
      if (this.currentScroll >= this.$refs.FooterRef.offsetTop - height) {
        this.isFooterShow = true;
      }
      else if (this.currentScroll >= this.$refs.ManufactureRef.offsetTop - height) {
        this.isManufactureShow = true;
      }
      else if (this.currentScroll >= this.$refs.IntroduceRef.offsetTop - height) {
        this.isIntroduceShow = true;
      }
      else if (this.currentScroll >= this.$refs.SellersRef.offsetTop - height) {
        this.isSellersShow = true;
      }
      else if (this.currentScroll >= this.$refs.PopularsRef.offsetTop - height + 100) {
        this.isPopularsShow = true;
        
      } 
    },
  }
}
</script>
<style lang='scss'>
.index-container {
  width: 100%;
  .green {
    color: $green !important;
  }
  .top-nav-m {
    display: none;
  }
  .top-nav {
    height: $headerHeight;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding: 0 60px;
    box-sizing: border-box;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 999;
    padding-top: $headerNotice;
    .top-nav-notice {
      width:100%;
      height:46px;
      position:absolute;
      top:0;
      background: $green;
      left: 0;
      color: #fff;
      font-size: 18px;
      text-align: center;
      line-height:46px;
      font-weight: 500;
    }
    .logo {
      height: 48px;
      &>img {
        height: 100%;
        width: auto;
      }
    }
    .nav-list {
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
      align-items: center;
      &>li {
        font-size: 20px;
        line-height: 13px;
        color: #FFFFFF;
        margin-right: 52px;
        cursor: pointer;
        font-weight: 500;
        &:last-child {
          margin-right: 0;
        }
        &:hover {
          color: $green;
          font-weight: bold;
        }
      }
      .active {
        font-weight: bold;
        color: $green;
      }
    }
  }
}
@media only screen and (max-width: 1200px) {
.index-container {
  .top-nav {
    .nav-list {
      &>li {
        margin-right: 35px;
      }
    }
  }
}
}
.part-swiper {
  width: 100%;
  height: 760px;
  .top-swiper {
    background: url(./../../assets/images/banner.png) no-repeat center;
    background-size: cover;
    width: 100%;
    height: 100%;
    position: relative;
    cursor: pointer;
    .top-swiper-text {
      color: #fff;
      position: absolute;
      bottom: 50px;
      font-size: 60px;
      width: 100%;
      text-align: center;
      font-weight: bold;
    }
  }
  .top-swiper2 {
    background: url(./../../assets/images/swiper1.jpg) no-repeat center;
    background-size: cover;
  }
  .top-swiper3 {
    background: url(./../../assets/images/swiper2.jpg) no-repeat center;
    background-size: cover;
  }
  .el-carousel, .el-carousel__container {
    height: 100%;
    .el-carousel__indicator--horizontal {
      padding: 12px 8px 20px;
    }
    .el-carousel__indicators {

      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: row;
    }
    .el-carousel__indicator {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: row;
      .el-carousel__button {
        width: 10px;
        height: 10px;
        border-radius: 50%;
        opacity: 1;

      }
    }
    .el-carousel__indicator.is-active button {
      width: 14px;
      height: 14px;
      background-color: $green;
    }
  }
}
@media only screen and (max-width: 1200px) {
.part-swiper {
  .top-swiper {
    .top-swiper-text {
      font-size: 50px;
    }
  }
}
}
@media only screen and (max-width: 1200px) {
.part-swiper {
  .top-swiper {
    .top-swiper-text {
      font-size: 38px;
    }
  }
}
}
.part-populars {
  margin: auto;
  padding: 0 60px;
  box-sizing: border-box;
  width: 100%;
  .popular-lists {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
  }
  .popular-lis {
    padding: 0 10px;
    width: 33.33%;
    height: 260px;
    margin-bottom: 20px;
  }
  .popular-items {
    position: relative;
    padding: 20px 20px 20px 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    cursor: pointer;
    &:hover {
      .popular-wrap {
        transform: translate(0px, 0);
      }
      .popular-title {
        opacity: 0;
        -khtml-opacity: 0;
        visibility: hidden;
        z-index: 0;
        -webkit-transform: translate(-5px, 0);
        transform: translate(-5px, 0);
      }
      .popular-textwrap {
        opacity: 1;
        -khtml-opacity: 1;
        -webkit-transform: translate(0, 0);
        transform: translate(0, 0);
        visibility: visible;
      }
    }
    .popular-wrap {
      transition: all 0.6s ease;
      position: absolute;
      left: 0;
      top: 0;
      height: 100%;
      transform: translate(-10px, 0);
      width: calc( 100% + 10px );
    }
    .popular-pics {
      width: auto;
      max-width: none;
      min-width: 100%;
      height: 100%;
      position: absolute;
      left: 50%;
      top: 50%;
      -webkit-transform: translate(-50%, -50%);
      transform: translate(-50%, -50%);
      object-fit: cover;
    }
    .popular-title {
      color: #fff;
      margin: 0;
      font-size: 22px;
      line-height: 28px;
      position: absolute;
      left: 20px;
      bottom: 10px;
      z-index: 2;
      -webkit-transition: all 0.4s ease;
      transition: all 0.4s ease;
      font-weight: 600;
    }
    .popular-textwrap {
      background: linear-gradient(to left, #78cab7 0%, rgba(255, 255, 255, 0) 100%);
      display: flex;
      width: 100%;
      height: 100%;
      position: relative;
      padding: 40px 10px 40px 20px;
      color: #fff;
      align-items: center;
      font-size: 18px;
      line-height: 24px;
      z-index: 1;
      -webkit-transition: all 0.4s ease;
      transition: all 0.4s ease;
      filter: alpha(opacity = 0);
      opacity: 0;
      -khtml-opacity: 0;
      visibility: hidden;
      -webkit-transform: translate(-30px, 0);
      transform: translate(-30px, 0);
    }
    .hpcglItemTextInner {
      max-width: calc(100% - 20px);
      font-size: 16px;
      line-height: 22px;
      color: #fff;
      .hpcglItemTitle {
        font-size: 20px;
        line-height: 26px;
        font-weight: bold;
        margin: 0 0 13px 0;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
      }
      .hpcglItemDesc {
        height: 110px;
        display: -webkit-box;
        -webkit-box-orient: vertical;
        overflow: hidden;
        -webkit-line-clamp: 5; /* 显示的行数 */
        font-weight: 500;
      }
      .hpcglItemBtnsWrap {
        display: flex;
        margin: 17px 0 0 0;
        font-size: 16px;
        line-height: 22px;
        .hpcglItemBtns {
          margin: 0 28px 0 0;
          padding: 0 0 7px 0;
          text-decoration: none;
          color: #fff;
          font-size: 16px;
          line-height: 24px;
          position: relative;
          font-weight: bold;
          &::after {
            content: '';
            background: #fff;
            width: 100%;
            height: 3px;
            position: absolute;
            bottom: 0;
            left: 0;
            -webkit-transition: all 0.2s ease;
            transition: all 0.2s ease;
          }
        }
      }
    }
  }
  .whole-popular-lis {
    padding: 0 10px;
    width: 100%;
    height: 260px;
    color: #fff;
    position: relative;
    overflow: hidden;
    transition: all 0.6s ease;
    cursor: pointer;
    .whole-popular-items, .whole-popular-wrap {
      width: 100%;
      height: 100%;
      transition: all 0.6s ease;
      overflow: hidden;
      &>img {
        width: 100%;
        height: 100%
      }
    }
    .whole-popular-centers {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      color: #fff;
      text-align: center;
      font-size: 26px;
      line-height: 1.6;
      width: 100%;
      z-index: 2;
      -webkit-transition: all 0.4s ease;
      transition: all 0.4s ease;
      font-weight: 500;
    }
  }

}
@media only screen and (max-width: 1200px) {
.part-populars {
  .whole-popular-lis {
    .whole-popular-items, .whole-popular-wrap {
      position: relative;
      &>img {
        width: auto;
        height: 100%;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
      }
    }
  }
}
}
.part-sellers {
  .sellers-lists {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 60px;
    width: 100%;
    .sellers-li-wrap {
      width: 25%;
        padding: 0 10px;
        .sellers-items {
          width: 100%;
          margin-right: 20px;
          padding: 20px;
          box-sizing: border-box;
          cursor: pointer;
          &:hover {
            .sellers-pics {
              &>img {
              transform: scale(1.1);
                
              }
            }
            .sellers-titles {
              color: $greenText;
            }
            .sellers-descs {
              color: $greenText;
            }
            .sellers-btns {
              background: $greenText;
            }
          }
          &:last-child {
            margin-right: 0;
          }
          .sellers-pics {
            width: 100%;
            overflow: hidden;
            position: relative;
            padding-top: 10px;
            &>img {
              width: 100%;
              height: auto;
              transition: all 0.3s ease;
            }
          }
          .sellers-titles {
            display: block;
            text-decoration: none;
            font-size: 20px;
            line-height: 24px;
            font-weight: bolder;
            margin: 12px 0 8px 0;
            text-align: center;
            transition: all 0.3s ease;
            color: #000;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
          }
          .sellers-descs {
            font-size: 14px;
            line-height: 20px;
            margin: 0 0 18px 0;
            transition: all 0.3s ease;
            text-align: center;
            display: -webkit-box;
            -webkit-box-orient: vertical;
            overflow: hidden;
            -webkit-line-clamp: 3; /* 显示的行数 */
            color: #000;
            font-weight: 500;
          }
          .sellers-btns {
            height: 40px;
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            cursor: pointer;
            background: $green;
            transition: all 0.3s ease;
            color: #FFFFFF;
          }
        }
    }
  }
  .all-products-view {
    padding: 60px 0;
  }
}
.part-introduce-pc {
  display: block;
}
.part-introduce-m {
  display: none;
}
.part-introduce {
  background: url(./../../assets/images/lab.png) no-repeat center;
  background-size: 100% 100%;
  width: 100%;
  height: max-content;
  color: #fff;
  padding-bottom: 80px;
  margin-top: 20px;
  .introduce-title {
    padding-top: 80px;
    font-size: 60px;
    font-weight: bolder;
    text-align: center;
  }
  .introduce-subtitle {
    text-align: center;
    font-size: 60px;
    font-weight: normal;
    margin-top: -10px;
  }
  .introduce-wrap {
    padding: 50px 70px 0;
    display: flex;
    width: 100%;
    .introduce-wrap-left {
      width: 60%;
      padding-right: 120px;
      .introduce-wrap-text {
        font-size: 20px;
        line-height: 3;
        font-weight: 500;
        position: relative;
        top: -7px;
      }
      .introduce-wrap-more {
        font-weight: 600;
        color: #fff;
        cursor: pointer;
        font-size: 22px;
        transition: all .6s;
        transform-origin: center left;
        &:hover {
          transform: scale(1.2);
        }
        &::after {
          content: '';
          display: inline-block;
          width: 12px;
          height: 12px;
          margin: 0 0 1px 5px;
          -webkit-transform: rotate(45deg);
          transform: rotate(45deg);
          border-top: 3px solid #fff;
          border-right: 3px solid #fff;
          -webkit-transition: all 0.2s ease;
          transition: all 0.2s ease;
        }
      }
    }
    .introduce-wrap-right {
      width: 40%;
      padding-left: 20px;
      .introduce-video {
        width: 100%;
        height: 100%;
        background-color: #fff;
        min-height: 250px;
        video {
          width: 100%;
          height: 100%;
          background: #000;
        }
      }
      .introduce-fullscreen {
        font-size: 22px;
        font-weight: 600;
        text-align: center;
        cursor: pointer;
        transition: all .6s;
        transform-origin: center;
        &:hover {
          transform: scale(1.2);
        }
      }
    }
  }
}
@media only screen and (max-width: 1200px) {
.part-introduce {
  .introduce-title {
    font-size: 55px;
  }
  .introduce-subtitle {
    font-size: 55px;
  }
  .introduce-wrap {
    .introduce-wrap-left {
      .introduce-wrap-text {
        line-height: 2.5;
      }
    }
  }
}
}
.part-Manufacture {
  padding-top: 90px;
  .manufacture-title {
    text-align: center;
    font-size: 50px;
    color: $greenText;
    font-weight: bolder;
  }
  .manufacture-subtitle {
    margin-top: 20px;
    text-align: center;
    line-height: 1.5;
    font-size: 25px;
    font-weight: normal;
  }
  .manufacture-content {
    display: flex;
    width: 100%;
    padding: 40px $padding 0;
    justify-content: space-between;
    .manufacture-swiper-content {
      width: calc( 50% - 10px );
      .manufacture-image {
        width: 100%;
        position: relative;
        overflow: hidden;
        border-radius: 12px;
        &>img {
          width: 100%;
          transition: all 0.6s ease;
          &:hover {
            transform: scale(1.2);
          }

        }
      }
      .manufacture-name {
        font-size: 25px;
        color: #000;
        padding-top: 28px;
        text-align: center;
        font-weight: 500;
      }
    }
  }
}
.view-all-Manufacturing {
  padding:40px 0px 30px;
}
@media only screen and (max-width: 1100px) {
.part-Manufacture {
  .manufacture-title {
    font-size: 40px;
  }
  .manufacture-subtitle {
    font-size: 22px;
  }
}
}
@media only screen and (max-width: 1200px) {

  .part-sellers {
  .sellers-lists {
    justify-content: flex-start;
    flex-wrap: wrap;
    .sellers-li-wrap {
      width: 33.33%;
    }
  }
}
}

@media only screen and (max-width: 900px) {
.index-container{
  padding-top: $headerHeightMobile;
  overflow-x: hidden;
  .top-nav-m {
    display: block;
  }
  .top-nav {
    display: none;
  }
  .part-swiper {
    height: 250px;
    .top-swiper {
      .top-swiper-text {
        bottom: 20px;
        font-size: 16px;
      }
    }
    .el-carousel, .el-carousel__container {
      .el-carousel__indicator--horizontal {
        padding: 12px 8px 6px 8px;
      }
      .el-carousel__indicator {
        .el-carousel__button {
          width: 8px;
          height: 8px;
        }
      }
      .el-carousel__indicator.is-active button {
        width: 11px;
        height: 11px;
      }
    }
  }

  .part-populars {
    padding: 0 15px;
    .popular-lis {
      padding: 0 5px;
      width: 50%;
      height: 120px;
      margin-bottom: 10px;
    }
    .popular-items {
      &:hover {
        // pointer-events: none;
        .popular-wrap {
          transform: unset;
        }
        .popular-title {
          opacity: 1;
          transform: unset;
        }
        .popular-textwrap {
          opacity: 1;
          transform: unset;
        }
      }
      .popular-wrap {
        transform: translate(0, 0);
        width: 100%;
      }
      .popular-title {
        font-size: 16px;
        line-height: 1.3;
        left: 10px;
        bottom: 6px;
      }
      .popular-textwrap {
        display: none;
      }
    }
    .whole-popular-lis {
      padding: 0 5px;
      height: 120px;
      .whole-popular-centers {
        font-size: 16px;
        line-height: 1.4;
      }
    }

  }


  .part-sellers {
    .sellers-lists {
      padding: 0 20px;
      flex-wrap: wrap;
      .sellers-li-wrap {
        width: 50%;
        padding: 0;
        .sellers-items {
          margin: 0;
          padding: 20px;
          &:hover {
            .sellers-pics {
              &>img {
                transform: unset;
              }
            }
          }
          .sellers-titles {
            font-size: 20px;
            line-height: 24px;
            margin: 12px 0 8px 0;
          }
          .sellers-descs {
            font-size: 14px;
            line-height: 20px;
            margin: 0 0 18px 0;
          }
          .sellers-btns {
            height: 40px;
          }
        }
      }
    }
    .all-products-view {
      padding: 30px 0;
    }
  }



  .part-introduce-pc {
    display: none;
  }
  .part-introduce-m {
    display: block;
  }
  .part-introduce {
    background: url(./../../assets/images/lab.png) no-repeat center;
    background-size: cover;
    padding-bottom: 20px;
    .introduce-title {
      padding-top: 20px;
      font-size: 24px;
      font-weight: 800;
      text-align: center;
    }
    .introduce-subtitle {
      font-size: 22px;
      margin-top: 0px;
    }
    .introduce-wrap {
      padding: 30px 20px 0;
      display: flex;
      width: 100%;
      .introduce-wrap-left {
        width: 100%;
        padding-right: 0;
        .introduce-wrap-text {
          font-size: 16px;
          line-height: 1.5;
          text-align: center;
        }
        .introduce-wrap-more {
          text-align: center;
          font-size: 18px;
          &:hover {
            transform: unset;
          }
          &::after {
            content: '';
            display: inline-block;
            width: 8px;
            height: 8px;
            margin: 0 0 1px 5px;
            border-top: 2px solid #fff;
            border-right: 2px solid #fff;
          }
        }
      }
      .introduce-wrap-right {
        display: none;
      }
    }
    .introduce-wrap-view {
      padding-top: 10px;
    }
  }


  .part-Manufacture {
    padding-top: 30px;
    .manufacture-title {
      font-size: 26px;
    }
    .manufacture-subtitle {
      margin-top: 20px;
      line-height: 1.4;
      font-size: 16px;
    }
    .manufacture-content {
      display: flex;
      width: 100%;
      padding: 20px 20px 0;
      justify-content: space-between;
      .manufacture-swiper-content {
        width: calc( 50% - 5px );
        .manufacture-image {
          border-radius: 0px;
          &>img {
            width: 100%;
            height: auto;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);
            &:hover {
              transform: unset;
            }

          }
        }
        .manufacture-name {
          font-size: 14px;
          padding-top: 10px;
        }
      }
    }
  }

  .view-all-Manufacturing {
    padding:20px 0px 10px;
  }

}
}
</style>