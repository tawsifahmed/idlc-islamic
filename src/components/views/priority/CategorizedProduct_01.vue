<template>
  <section>
    <!--CATEGORIZED PORDUCT Part Start-->
    <div class="category">
      <!-- <div class="top_curve"></div> -->
      <div class=" categoryBg">
        <div class="container-lg">
          <div class="categoryBody">
            <div class="header sectionTitle">
              <h2 class="h2Responsive ">Services We Offer</h2>
            </div>
            <div class="container">
              <form class="categoryForm">
                <div class="form-group row justify-content-center">
                  <label class="col-sm-12 col-form-label category_label">I want to take a loan for</label>
                  <div class="col-md-6 col-sm-12">
                    <div class="custom-select">
                      <select class="" id="selectProductsItem2">
                        <option>Select One</option>
                        <option value="0">Renovating my home</option>
                        <option value="1">Purchasing Insurance for my home</option>
                        <option value="2">Constructing a new home</option>
                        <option value="3">Building a house (with limited EMI)</option>
                        <option value="4">Building a semi-paka house</option>
                        <option value="5">Purchasing a bungalow</option>
                        <option value="6">Purchasing space for business/commercial activity</option>
                      </select>
                    </div>
                  </div>
                </div>

              </form>
              <div class="categories">
                <div :data-id="itemData.id" @click="onClickProduct(itemData.id)" class="productsItem reason" v-for="itemData in productData" :key="itemData.id">
                  <a>
                    <h6>{{ itemData.name }}</h6>
                    <img alt="Retirement" :src="itemData.image">
                    <div class="nextArrow">
                      <a>
                        <div class="arrow"></div>
                      </a>
                    </div>
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="bottom_curve"></div> -->
    </div>
    <!-- <div id="topBreak"></div> -->
    <!--CATEGORIZED PORDUCT Part End-->
    <div class="productFeatures">

      <div v-for="(itemData, index)  in productData" class="categoryDetails " :id="'categoryFeature'+index" ref="'id_'+itemData.id" :key="'categoryFeature'+index">
        <span @click="categoryPrevButton(index)" class="categoryPrevButton" :data-id="itemData.id"><a><span class="icon-arrow-left"></span></a></span>
        <span @click="categoryNextButton(index)" class="categoryNextButton" :data-id="itemData.id"><a><span class="icon-arrow-right"></span></a></span>
        <div class="container-lg">
          <div class="productPageTitleDetai sectionTitle">
            <h2 style="text-align: center; " class="h2Responsive ">
              {{ itemData.name }}
            </h2>
            <h6 class="categoriesTagline">{{ itemData.product_tagline }}</h6>
            <span  v-html="itemData.description"></span>

          </div>
        </div>

        <div class="container-lg">
          <div class="tab">
            <button class="tablinks1 active" @click="openTab( 'feature'+itemData.id, $event)" :id="'defaultOpen'+itemData.id">Key Feature</button>
          </div>

          <div :id="'feature'+itemData.id" class="tabcontent1" style="display: block;">
            <span  v-html="itemData.feature_description" ></span>
            <router-link to="/get-in-touch-with-us" class="tabcontent1Button">Get in Touch</router-link>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>
<script>
  import axios from "axios";

  export default {
    name: "CategorizedProduct",
    data() {
      return {
        prev: "<span class='icon-chevron-left'></span>",
        next: "<span class='icon-chevron-right'></span>",
        shortcode: 'Priority',
        isMobile: false,
        productData: [],
        ProductDetailData: [],

      }
    },
    methods: {

      onClickProduct(selectedId){
        $(".categoryDetails").hide();
        $("#categoryFeature"+selectedId).show(700);
        $( "#defaultOpen"+selectedId ).trigger( "click" );
        //initiate as false
        // device detection
        if(/(android|bb\d+|meego).+mobile|avantgo|bada\/|blackberry|blazer|compal|elaine|fennec|hiptop|iemobile|ip(hone|od)|ipad|iris|kindle|Android|Silk|lge |maemo|midp|mmp|netfront|opera m(ob|in)i|palm( os)?|phone|p(ixi|re)\/|plucker|pocket|psp|series(4|6)0|symbian|treo|up\.(browser|link)|vodafone|wap|windows (ce|phone)|xda|xiino/i.test(navigator.userAgent)
          || /1207|6310|6590|3gso|4thp|50[1-6]i|770s|802s|a wa|abac|ac(er|oo|s\-)|ai(ko|rn)|al(av|ca|co)|amoi|an(ex|ny|yw)|aptu|ar(ch|go)|as(te|us)|attw|au(di|\-m|r |s )|avan|be(ck|ll|nq)|bi(lb|rd)|bl(ac|az)|br(e|v)w|bumb|bw\-(n|u)|c55\/|capi|ccwa|cdm\-|cell|chtm|cldc|cmd\-|co(mp|nd)|craw|da(it|ll|ng)|dbte|dc\-s|devi|dica|dmob|do(c|p)o|ds(12|\-d)|el(49|ai)|em(l2|ul)|er(ic|k0)|esl8|ez([4-7]0|os|wa|ze)|fetc|fly(\-|)|g1 u|g560|gene|gf\-5|g\-mo|go(\.w|od)|gr(ad|un)|haie|hcit|hd\-(m|p|t)|hei\-|hi(pt|ta)|hp( i|ip)|hs\-c|ht(c(\-| ||a|g|p|s|t)|tp)|hu(aw|tc)|i\-(20|go|ma)|i230|iac( |\-|\/)|ibro|idea|ig01|ikom|im1k|inno|ipaq|iris|ja(t|v)a|jbro|jemu|jigs|kddi|keji|kgt( |\/)|klon|kpt |kwc\-|kyo(c|k)|le(no|xi)|lg( g|\/(k|l|u)|50|54|\-[a-w])|libw|lynx|m1\-w|m3ga|m50\/|ma(te|ui|xo)|mc(01|21|ca)|m\-cr|me(rc|ri)|mi(o8|oa|ts)|mmef|mo(01|02|bi|de|do|t(\-| |o|v)|zz)|mt(50|p1|v )|mwbp|mywa|n10[0-2]|n20[2-3]|n30(0|2)|n50(0|2|5)|n7(0(0|1)|10)|ne((c|m)\-|on|tf|wf|wg|wt)|nok(6|i)|nzph|o2im|op(ti|wv)|oran|owg1|p800|pan(a|d|t)|pdxg|pg(13|\-([1-8]|c))|phil|pire|pl(ay|uc)|pn\-2|po(ck|rt|se)|prox|psio|pt\-g|qa\-a|qc(07|12|21|32|60|\-[2-7]|i\-)|qtek|r380|r600|raks|rim9|ro(ve|zo)|s55\/|sa(ge|ma|mm|ms|ny|va)|sc(01|h\-|oo|p\-)|sdk\/|se(c(\-|0|1)|47|mc|nd|ri)|sgh\-|shar|sie(\-|m)|sk\-0|sl(45|id)|sm(al|ar|b3|it|t5)|so(ft|ny)|sp(01|h\-|v\-|v )|sy(01|mb)|t2(18|50)|t6(00|10|18)|ta(gt|lk)|tcl\-|tdg\-|tel(i|m)|tim\-|t\-mo|to(pl|sh)|ts(70|m\-|m3|m5)|tx\-9|up(\.b|g1|si)|utst|v400|v750|veri|vi(rg|te)|vk(40|5[0-3]|\-v)|vm40|voda|vulc|vx(52|53|60|61|70|80|81|83|85|98)|w3c(\-| )|webc|whit|wi(g |nc|nw)|wmlb|wonu|x700|yas\-|your|zeto|zte\-/i.test(navigator.userAgent.substr(0,4))) {
          this.isMobile = true;
        }
        if(this.isMobile){
          $('html, body').animate({
            scrollTop: $("#categoryFeature"+selectedId).offset().top- 40
          }, 2000);
        }else{
          $('html, body').animate({
            scrollTop: $("#categoryFeature"+selectedId).offset().top- 22
          }, 2000);
        }
      },

      openTab(cityName, event) {
        var i, tabcontent, tablinks;
        tabcontent = document.getElementsByClassName("tabcontent1");
        for (i = 0; i < tabcontent.length; i++) {
          tabcontent[i].style.display = "none";
        }
        tablinks = document.getElementsByClassName("tablinks1");
        for (i = 0; i < tablinks.length; i++) {
          tablinks[i].className = tablinks[i].className.replace(" active", "");
        }
        document.getElementById(cityName).style.display = "block";
        event.target.className += " active";
      },

      categoryNextButton(id){
        let nextId = id+1;
        $(".categoryDetails").hide();
        if (nextId <= this.productData.length -1){
          $("#categoryFeature"+nextId).show(700);
          $( "#defaultOpen"+nextId ).trigger( "click" );
        }else{
          nextId = 0;
          $("#categoryFeature"+nextId).show(700);
          $( "#defaultOpen"+nextId ).trigger( "click" );
        }
      },

      categoryPrevButton(id) {
        let prevId = id-1;
        $(".categoryDetails").hide();
        if (prevId >= 0){
          $("#categoryFeature"+prevId).show(700);
          $( "#defaultOpen"+prevId ).trigger( "click" );
        }else{
          prevId = this.productData.length -1;
          $("#categoryFeature"+prevId).show(700);
          $( "#defaultOpen"+prevId ).trigger( "click" );
        }
      },

      getProducts() {
        axios.get('get-product', {
          params: {
            shortcode: this.shortcode
          }
        }).then((response) => {
          if (response.status == 200) {
            this.productData = response.data.details;

          }
        }).catch(error => console.log(error));
      }
    },
    created() {
      this.getProducts();
    }
  }
</script>
<style lang="" scoped>
 .category {
  position: relative;
  background-attachment: fixed;
  background-size: 100% auto;
  position: relative;
  margin-bottom: 0px;
}
.categoryBg {
  padding: 30px 75px 0px 75px;
}

.categoryBg .categoryBody {
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
  text-align: center;
  border-radius: 10px;
}

.category .top_curve {
  background: url('~@/assets/img/curveShapeWhite.png') top center;
  top: 0rem;
  background-size: cover;
  height: 5rem;
  width: 100%;
  position: absolute;
  z-index: 100;
}

.category_label {
  font-size: 14px;
  text-align: center;
  padding-top: 0;
}

.category .bottom_curve {
  background: url('~@/assets/img/curveShapeWhiteUp.png') top center;
  bottom: 0rem;
  background-size: cover;
  height: 5rem;
  width: 100%;
  position: absolute;
  z-index: 100;
}

.categoryBody .header {
  color: #333;
  text-transform: uppercase;
  margin-bottom: 20px;
}
.categoryBody .categories {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.categoryBody .categories .reason {
  flex-basis: 23%;
  background: rgba(214, 46, 47, 0.95);
  margin: 10px;
  color: #fff;
  padding: 15px;
  border-radius: 5px;
  transition: all 0.3s;
  cursor: pointer;
}
.categoryBody .categories .reason:hover {
  background: rgba(214, 46, 47, 1);
}
.categoryBody .categories .reason a h6 {
  color: #fff;
}
.categoryBody .categories .reason a img {
  transition: all 0.3s;
  height: 80px;
}

.categoryBody .nextArrow a .arrow {
  height: 30px;
  width: 30px;
  margin: 10px auto;
  background-image: url("~@/assets/img/catagories/Arrow-01.png");
  background-size: 100% 100%;
  transition: all 0.3s;
}
.categoryBody .reason a {
  text-decoration: none;
}

.categoryBody .reason:hover .nextArrow a .arrow {
  background-image: url("~@/assets/img/catagories/Arrow-02.png");
  transform: translateX(0px);
}
.categoryBody .reason:hover a img {
  transform: scale(1.15);
}

.reason i {
  color: darkred;
  margin-top: 15px;
}

  .rightToLeftAnimation{
    display: block!important;
    font-size: 200%;
    animation: rightToLeft .9s ease-in-out forwards;
  }

  .productFeatures .categoryDetails {
    display: none;
  }

  .productFeatures .categoryDetails:first-child {
    display: block;
  }


  .custom-select select {
    display: none;
  }

  .categoryBody .mcategory .reason {
    flex-basis: 23%;
    background: rgba(214, 46, 47, 0.95);
    background: #333;
    margin: 10px;
    color: #fff;
    padding: 15px;
    border-radius: 5px;
    transition: all 0.3s;
  }

  .categoryBody .mcategory .reason:hover {
    background: #333;
  }

  .categoryBody .mcategory .reason a {
    display: block;
    text-align: center;
  }

  .categoryBody .mcategory .reason a h6 {
    color: #fff;
  }

  .categoryBody .mcategory .reason a img {
    transition: all 0.3s;
    height: 80px;
    width: 80px;
    display: inline-block;
  }

  .categoryBody .mcategory .owl-buttons {
    padding-top: 15px !important;
    position: absolute;
    left: 50%;
    /* padding-right: 45px !important; */
  }

  .categoriesTagline {
    margin-top: 13px;
    font-size: 1.25rem;
  }

  .categories {
    display: flex;
  }

  .mcategory {
    display: none;
  }



  @media screen and (max-width: 770px) {
    .categories {
      display: none !important;
    }

    .mcategory {
      display: block !important;
    }
  }

  .categoryBody .categories .reason {
    background: #333;

}
  .categoryBody .categories .reason:hover {
    background: rgba(51, 51, 51, 0.90);
}
.productFeatures .tab {
    border-bottom:2px solid #333;
}
.productFeatures .tab button.active {
    background-color: #333;
}
.productFeatures .tabcontent1 .tabcontent1Button {
    border: 2px solid #333;
}
.productFeatures .tabcontent1 .tabcontent1Button:hover {
    background: #333;
}
.categoryBody .reason:hover .nextArrow a .arrow {
  background-image: url("~@/assets/img/catagories/Arrow-03.png");
  transform: translateX(0px);
}
.categoryBody .mcategory .reason[data-v-3261939d] {
    background: #333;
}
@media screen and (max-width: 600px){
  .productFeatures .tab .tablinks1:first-child, .productFeatures .tab .tablinks1:nth-child(2) {
  border-bottom: 1px solid #000;
  border-right: 1px solid #000;
}

  .select-selected-black{
    background: #333 !important;
  }

  .productPageTitleDetai {
    padding: 50px 0;
  }

}

</style>
