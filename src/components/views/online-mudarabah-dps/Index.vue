<template>
  <div>
    <app-header />
    <app-header-mobile />
    <app-side-nav />
    <app-top-curve />
    <app-slider />
    <!--    //page heading start-->
    <div class="container homePageTitleDetails sectionTitle">
      <h2 style="text-align: center; " class="h2Responsive ">
        {{ contentData.second_title }}
      </h2>
      <h6>{{ contentData.tagline }}</h6>
      <span class="product-description" v-html="contentData.description"></span>
    </div>
    <!--    //page heading end-->


    <!-- comment out -->
    <!--  -->
    <!--  -->

    <!-- <app-categorized-product class="mb-5" />

    <div>
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div class="header sectionTitle text-uppercase text-center">
              <h2 class="h2Responsive" style="margin-bottom: 30px;">PSR Table</h2>
            </div>
            <div v-html="depositPSR" style="overflow-x: auto;"></div>
          </div>
        </div>
      </div>
    </div>
    <br>
    <br>
    <app-previous-profit :depoPrevProfits="depoPrevProfits"/>
    <app-deposit-calculator />
    <app-faq-tab /> -->

    <!--  -->
    <!--  -->
    <!-- comment out -->




    <!-- <app-e-m-i-calculator/> -->
    <!-- <app-common-w-h-tab/> -->
    <!-- <app-related-product/> -->

    <app-footer />


  </div>
</template>

<script>
import axios from "axios";


export default {
  metaInfo: {
    title: 'Online Mudarabah DPS',
    meta: [
      { name: 'description', content: 'Online Mudarabah DPS' },
      { name: 'keywords', content: 'Islamic Deposits, IDLC Islamic, Financing Products, Islamic Finance, Interest Rate' },
    ]
  },
  name: 'online-mudarabah-deposit',
  data() {
    return {
      shortcode: 'OnlineMudarabahDPS',
      relatedProductData: [],
      isMobile: false,
      contentData: "",
      faqTabName: 'Online Mudarabah DPS',
      depositPSR: null,
      depoPrevProfits: null,
    }
  },
  components: {
    AppHeaderMobile: () => import('../../incudes/HeaderMobile'),
    AppHeader: () => import('../../incudes/Header'),
    AppSideNav: () => import('../../incudes/SideNav'),
    AppTopCurve: () => import('../../incudes/TopCurve'),
    AppSlider: () => import('../../incudes/Slider'),
    AppCategorizedProduct: () => import('../../partials/CategorizedProducts'),
    AppEMICalculator: () => import('../../partials/EMICalculator'),
    AppDepositCalculator: () => import("../calculators/DepositCalculator"),
    // AppWHTab: () => import('./WHTab'),
    AppPreviousProfit: () => import('./PrevProfitTab'),
    AppFaqTab: () => import('./TabComponent'),
    AppCommonWHTab: () => import('../../partials/CommonWHTab'),
    AppRelatedProduct: () => import('../../partials/RelatedProduct'),
    AppFooter: () => import('../../incudes/Footer'),


  },
  methods: {
    getRelatedProducts() {
      axios.get('get-related-product', {
        params: {
          shortcode: this.shortcode
        }
      }).then((response) => {
        if (response.status == 200) {
          this.relatedProductData = response.data.details;
        }
      }).catch(error => console.log(error));
    },

    getHeaderContent() {
      axios.get('get-page-content', {
        params: {
          shortcode: this.shortcode
        }
      }).then((response) => {
        if (response.status == 200) {
          this.contentData = response.data.details;
        }
      }).catch(error => console.log(error));
    },
    getDepositPSR() {
      axios.get('deposite-page-asset').then((response) => {
        if (response.status == 200) {
          this.depositPSR = response.data.data.psr_table;
          this.depoPrevProfits = response.data.data.tabs;
          // console.log('this.depositPSR', response);
        }
      }).catch(error => console.log(error));
    }
  },
  created() {
    this.getHeaderContent();
    this.getRelatedProducts();
    this.getDepositPSR();

  },
  mounted() {
    var scripts = [
      "https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.4.0/Chart.min.js",
      "https://code.highcharts.com/stock/modules/data.js"
    ];
    scripts.forEach(script => {
      let tag = document.createElement("script");
      tag.setAttribute("src", script);
      document.head.appendChild(tag);
    });
  },

}
</script>
<style scoped>
.product-description {
  font-size: 14px;
}


.all-report {
  width: 100%;
display: flex;
justify-content: flex-start;
flex-wrap: wrap;
}
.all-report li{
flex-basis: 15% !important;
flex-shrink: 0;
flex-grow: 0;
margin-left: 20px;

}
.all-report_q {
justify-content: center;
}
.all-report_q li {
flex-basis: 10% !important;
}
@media screen and (max-width: 600px){
.all-report {
justify-content: space-around;
flex-wrap: wrap;
}
.all-report li{
flex-basis: 35% !important;
margin-left: 0px;
}
.all-report_q {
justify-content: space-around;
}
.all-report_q li {
flex-basis: 35% !important;
}
}
.all-report_q li:first-child {
margin: 0 !important;
}
.all-report li > a{
display: block;
width: 100%;
}
.all-report li > a .f_icon{
background: #eeeeee;
padding: 15px;
border-radius: 100px;
transition: all 0.3s;
}
.all-report li > a .title{
height: 60px;
overflow: hidden;
}
.all-report li > a .title{
text-align: center;
}
.all-report li > a:hover .f_icon{
background: #8bdce4;
}
.all-report li > a > .f_icon img{
width: 100%;
}
.all-report li > a .d_icon{
height: 30px;
width: 30px;
margin: auto;
background-image: url("./../../../assets/img/financial-report/download-icon-02.png");
background-size: contain;
}
.all-report li > a:hover .d_icon{
background-image: url("./../../../assets/img/financial-report/download-icon-01.png");
}

.acb1 > .card-body{
  padding:  0px !important;
}

.tab_title{
  color: #000 !important;
}
</style>
