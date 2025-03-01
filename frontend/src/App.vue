<template>
  <div id="app">
    <!-- 導覽列 -->
    <nav class="navbar navbar-expand-lg fixed-top" :class="{ 'navbar-scrolled': isScrolled }">
      <div class="container">
        <a class="navbar-brand" href="#">宏家科技</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
          aria-controls="navbarNav" aria-expanded="false" aria-label="切換導航">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <a class="nav-link" href="#" @click.prevent="scrollToSection('services')">服務項目</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#" @click.prevent="scrollToSection('products')">產品介紹</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#" @click.prevent="scrollToSection('contact')">聯絡宏家</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <!-- 頂部 Hero 區塊 -->
    <section class="hero text-white text-center d-flex align-items-center">
      <div class="container">
        <h1 class="display-3 fw-bold">{{ title }}</h1>
        <p class="lead" v-html="subtitle"></p>
      </div>
    </section>

    <!-- 營業項目 -->
    <section id="services" class="py-5 bg-light">
      <div class="container">
        <h2 class="text-center fw-bold mb-4">營業項目</h2>
        <div class="row row-cols-1 row-cols-md-3 g-4">
          <div v-for="service in services" :key="service.title" class="col">
            <div class="card h-100 shadow-sm border-0" @click="openCard(service)">
              <div class="image-container">
                <img :src="service.image" alt="服務圖片" class="card-img-top img-fluid" />
              </div>
              <div class="card-body text-center">
                <h5 class="card-title">{{ service.title }}</h5>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 產品介紹 -->
    <section id="products" class="py-5">
      <div class="container">
        <h2 class="text-center fw-bold mb-4">產品介紹</h2>

        <!-- 第一張圖片 -->
        <div class="text-center mb-4">
          <img src="@/assets/product1.png" alt="Analog & Power Line Cards" class="img-fluid" />
        </div>

        <!-- 第二張圖片 -->
        <div class="text-center">
          <img src="@/assets/product2.png" alt="Highend/Memory Line Cards" class="img-fluid" />
        </div>
        <!-- 第三張圖片 -->
        <div class="text-center">
          <img src="@/assets/product3.png" alt="Wireless Line Cards" class="img-fluid" />
        </div>
        <!-- 第四張圖片 -->
        <div class="text-center">
          <img src="@/assets/product4.png" alt="Interconnect Line Cards" class="img-fluid" />
        </div>
        <!-- 第五張圖片 -->
        <div class="text-center">
          <img src="@/assets/product5.png" alt="Emech Line Cards" class="img-fluid" />
        </div>
        <!-- 第六張圖片 -->
        <div class="text-center">
          <img src="@/assets/product6.png" alt="Lighting Solutions" class="img-fluid" />
        </div>
        <!-- 第七張圖片 -->
        <div class="text-center">
          <img src="@/assets/product7.png" alt="Passive Line Cards" class="img-fluid" />
        </div>
      </div>
      <!-- 回到頂部按鈕 -->
      <button v-if="showBackToTop" @click="scrollToTop" class="back-to-top">
        ↑
      </button>
    </section>

    <!-- <section id="products" class="py-5">
      <div class="container">
        <h2 class="text-center fw-bold mb-4">產品介紹</h2>
        <div class="row row-cols-1 row-cols-md-3 g-4">
          <div v-for="product in products" :key="product.name" class="col">
            <div
              class="card h-100 shadow-sm border-0"
              @click="openCard(product)"
            >
              <div class="image-container">
                <img
                  :src="product.image"
                  alt="產品圖片"
                  class="card-img-top img-fluid"
                />
              </div>
              <div class="card-body text-center">
                <h5 class="card-title">{{ product.name }}</h5>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section> -->

    <!-- 聯絡我們 -->
    <section id="contact" class="contact py-5 text-white bg-dark">
      <div class="container d-flex flex-column flex-md-row align-items-center justify-content-between">
        <!-- 左側：聯絡資訊 -->
        <div class="contact-info text-center text-md-start">
          <h3 class="fw-bold mb-2">聯絡宏家</h3>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i> {{ contact.name }}
          </p>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i> {{ contact.eng_name }}
          </p>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i> 統一編號：{{ contact.tax }}
          </p>
          <br>
          <h3 class="fw-bold mb-2">聯絡電話</h3>
          <p class="mb-1">
            <i class="bi bi-telephone-fill"></i> 銷售窗口
          </p>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i> {{ contact.person_1 }}
          </p>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i> {{ contact.person_2 }}
          </p>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i> 業務信箱
          </p>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i>{{ contact.email }}
          </p>
          <p class="mb-1">
            <i class="bi bi-geo-alt-fill"></i> 聯絡地址
          </p>
          <p class="mb-1">
            <i class="bi bi-envelope-fill"></i>{{ contact.address }}
          </p>
        </div>

        <!-- 右側：Google 地圖 -->
        <div class="map-container">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d14484.795461175385!2d121.0054238215072!3d24.822871947259348!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3468368cf667477d%3A0x5b2e89b4389846a4!2z5Lit5bSZ6YeM!5e0!3m2!1szh-TW!2stw&dirflg=d"
            width="100%" height="300" style="border: 0" allowfullscreen="" loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
      </div>
    </section>

    <!-- 放大卡片視窗 -->
    <div v-if="isCardOpen" class="overlay" @click="closeCard">
      <div class="expanded-card">
        <img :src="selectedCard.image" alt="放大圖片" class="expanded-img" />
        <h5 class="expanded-title">
          {{ selectedCard.title || selectedCard.name }}
        </h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "宏家科技",
      subtitle:
        "宏家科技 (AiSee Technology) 成立於2023年，主要服務項目為各類型電子料的排單&現貨銷售。<br>" +
        "電子料包含：主動IC/被動元件/連接器/感測器/模組…等等。<br>"+
        "我們提供的產品適用於各種產業應用領域。<br>" +
        "例如：IC測試廠、SMT廠、通訊、電腦、消費電子、醫療、工控、穿戴裝置、AI等等。",
      showBackToTop: false,
      // 營業項目
      services: [
        {
          title:
            "全球電子料採購供應鏈與銷售服務(主動IC/被動元件/連接器/感測器/模組..)",
          image: new URL("@/assets/service1.png", import.meta.url).href,
        },
        {
          title: "提供急單/散料/現貨/排單需求",
          image: new URL("@/assets/service2.png", import.meta.url).href,
        },
        {
          title: "為專案批量試產的客户備齊BOM上電子料",
          image: new URL("@/assets/service3.png", import.meta.url).href,
        },
        {
          title: "提供客戶BOM表優化方案(協尋停產料/替代料)",
          image: new URL("@/assets/service4.png", import.meta.url).href,
        },
        {
          title: "代銷呆滯庫存(貨源:代理商/終端客戶)",
          image: new URL("@/assets/service5.png", import.meta.url).href,
        },
      ],

      // 產品介紹
      // products: [
      //   {
      //     name: "電子元件1",
      //     image: new URL("@/assets/product1.png", import.meta.url).href,
      //   },
      //   {
      //     name: "電子元件2",
      //     image: new URL("@/assets/product2.png", import.meta.url).href,
      //   },
      //   {
      //     name: "電子元件3",
      //     image: new URL("@/assets/product3.png", import.meta.url).href,
      //   },
      // ],

      // 聯絡方式
      contact: {
        name: "宏家科技有限公司",
        eng_name: "(AiSee Technology co.,Ltd)",
        tax: "93551295",
        email: "Aisee_0518@protonmail.com",
        person_1: "Amber +886-960-792909",
        person_2: "Ariel +886-953-111646",
        address: "新竹縣竹北市光明十街139號1F",
      },

      isCardOpen: false, // 控制放大視窗是否開啟
      selectedCard: {}, // 被選中的卡片數據
    };
  },
  methods: {
    openCard(item) {
      this.selectedCard = item;
      this.isCardOpen = true;
    },
    closeCard() {
      this.isCardOpen = false;
    },
    handleScroll() {
      this.showBackToTop = window.scrollY > 300;
    },
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: "smooth" });
    },
    scrollToSection: (sectionId) => {
      const section = document.getElementById(sectionId);
      if (section) {
        section.scrollIntoView({ behavior: "smooth" });
      }
    },
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rajdhani:wght@700&display=swap");

/* Top 區塊 */
.hero {
  background: linear-gradient(135deg, #ffffff, #000000);
  min-height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Top 字體*/
.hero h1 {
  background: linear-gradient(135deg, #0072bc 50%, #000 50%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* 服務 & 產品卡片 */
.card {
  transition: transform 0.3s, box-shadow 0.3s;
  border-radius: 10px;
  overflow: hidden;
  cursor: pointer;
}

/*Card back*/
.card:hover {
  transform: scale(1.05);
  box-shadow: 2px 2px 10px rgba(253, 251, 251, 0.2);
}

/* 圖片樣式 */
.image-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px;
}

.card-img-top {
  max-height: 120px;
  object-fit: contain;
  width: 100%;
  padding: 5px;
}

/* 放大視窗 */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1050;
  cursor: pointer;
}

.expanded-card {
  background: white;
  padding: 20px;
  border-radius: 10px;
  max-width: 500px;
  text-align: center;
  box-shadow: 0 5px 15px rgba(255, 255, 255, 0.3);
}

.expanded-card img {
  width: 100%;
  max-height: 250px;
  object-fit: contain;
  border-radius: 10px;
}

.expanded-title {
  font-size: 1.5em;
  margin-top: 10px;
}

/* 回到頂部按鈕 (圓形 + 美觀設計) */
.back-to-top {
  position: fixed;
  bottom: 40px;
  right: 20px;
  width: 50px;
  height: 50px;
  background: rgba(0, 0, 0, 0.6);
  color: white;
  border: none;
  border-radius: 50%;
  font-size: 24px;
  font-weight: bold;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
}

/*懸停時變化 */
.back-to-top:hover {
  background: rgba(0, 0, 0, 0.8);
  transform: scale(1.1);
}

/* 按下時縮小效果 */
.back-to-top:active {
  transform: scale(0.95);
}

/* 手機適應 */
@media (max-width: 768px) {
  .back-to-top {
    width: 45px;
    height: 45px;
    font-size: 20px;
  }
}

/* 響應式設計 */
@media (max-width: 768px) {
  .row-cols-md-3>.col {
    flex: 0 0 100%;
    max-width: 100%;
  }
}

/* Navbar */
.navbar {
  transition: all 0.3s ease-in-out;
  background: transparent;
}

/*navbar text*/
.navbar-scrolled {
  background: rgba(0, 0, 0, 0.8);
}

/*navbar text back*/
.navbar .nav-link {
  color: rgb(0, 0, 0);
  /* 預設文字顏色 */
  transition: color 0.3s ease-in-out;
  /* 平滑變化 */
}

/*navbar text back*/
.navbar .nav-link:hover {
  color: #0072bc;
  /* 滑鼠移過去變成藍色 */
}

/* 調整聯絡我們的容器 */
.contact .container {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

/* 在桌機上並排顯示 */
@media (min-width: 768px) {
  .contact .container {
    flex-direction: row;
    text-align: left;
  }

  .contact-info {
    flex: 1;
    /* 左邊的聯絡資訊佔據 50% */
    padding-right: 20px;
  }

  .map-container {
    flex: 1;
    /* 右邊的地圖佔據 50% */
    max-width: 500px;
    /* 限制最大寬度 */
  }
}

/* Google Maps 樣式 */
.map-container {
  width: 100%;
  max-width: 500px;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.map-container iframe {
  width: 100%;
  height: 300px;
  border: none;
}
</style>
