<template>
  <div class="container">
    <!-- Navbar -->
    <nav class="navbar">
      <div>
        <h1 class="name">PIXELINK</h1>
        <h3 class="base">Print Lab</h3>
      </div>

      <ul :class="{ open: menuOpen }">
        <li><a href="#services" @click="toggleMenu">Services</a></li>
        <li><a href="#gallery" @click="toggleMenu">Gallery</a></li>
        <li><a href="#contact" @click="toggleMenu">Contact</a></li>
      </ul>
    </nav>

    <!-- Hero Section with Slideshow -->
    <section class="hero">
      <div class="slideshow">
        <div
          v-for="(image, index) in images"
          :key="index"
          class="slide"
          :class="{ active: index === currentSlide }"
          :style="{ backgroundImage: 'url(' + image + ')' }"
        ></div>
      </div>
      <div class="hero-content">
        <h1>Premium T-Shirts for Boys</h1>
        <p>High-quality designs, stylish & comfortable</p>
        <a href="#contact" class="btn">Shop Now</a>
      </div>
    </section>

    <!-- About Section -->
    <section id="services" class="section">
      <h1 style="font-weight: bolder;">About Us</h1>
      <div class="grid">
        <div class="card">
          <h3>
            At PIXELINK, we specialize in premium custom T-shirt printing and a wide range of printing solutions tailored to your needs. Whether you need Screen Printing, Puff Printing, 3D Printing, DTF Stickers, Vinyl Stickers, High-Visible Reflective Stickers, or Rhinestone designs, we’ve got you covered!
          </h3>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="section">
      <h1 style="font-weight: bolder;">Our Services</h1>
      <div class="grid">
        <div class="card">
          <h3 style="font-weight: bolder;">Custom Designs</h3>
          <p>Get your own personalized T-shirt designs.</p>
        </div>
        <div class="card">
          <h3 style="font-weight: bolder;">Bulk Orders</h3>
          <p>Special discounts for bulk purchases.</p>
        </div>
        <div class="card">
          <h3 style="font-weight: bolder;">Fast Shipping</h3>
          <p>Quick and secure delivery across Pakistan.</p>
        </div>
      </div>
    </section>

    <!-- Gallery Section -->
    <section id="gallery" class="section">
      <h1 style="font-weight: bolder;">Gallery</h1>
      <div class="grid gallery">
        <img src="/g6.jpeg" alt="Shirt" />
        <img src="/g1.jpeg" alt="" />
        <img src="/g2.jpeg" alt="" />
        <img src="/g3.jpeg" alt="" />
        <img src="/g4.jpeg" alt="" />
        <img src="/g5.jpeg" alt="Shirt" />

      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <section id="contact" class="section">
        <h2>Contact Us</h2>
        <p>Location: Sialkot, Pakistan</p>
        <p>Email: <a href="mailto:pixelink8@gmail.com">pixelink8@gmail.com</a></p>
        <p>Phone: 0341 4799903</p>
      </section>
      <p>&copy; 2025 PIXELINK. All Rights Reserved.</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuOpen: false,
      images: [
        "/banner.jpeg",
        "/banner2.jpeg",
        "/banner3.jpeg",
        "/banner1.jpeg",
      ],
      currentSlide: 0,
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.images.length;
    },
  },
  mounted() {
    setInterval(this.nextSlide, 3000); // Change slide every 3 seconds
  },
};
</script>

<style>
/* General Styles */
.name {
  font-style: italic;
  font-size: 40px;
  font-weight: bolder;
}

.base {
  font-style: italic;
  margin-left: 104px;
}

/* Navbar */
.navbar {
  background: #333;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 1000;
}

.navbar ul {
  list-style: none;
  display: flex;
  gap: 20px;
}

.navbar ul li a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}

/* Hero Section */
.hero {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
  padding: 20px;
  position: relative;
  width: 100%;
  overflow: hidden;
}

/* Slideshow */

/* Slideshow */
.slideshow {
  position: absolute;
 justify-content: center;
   top:15%;
  width: 100%;
  height: 100%;
  overflow: visible;
}

.slide {
  position: absolute;
  width: 100%;
  height: 100%;
  background-size: 100% 100%; /* Stretch to fit */
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0;
  transition: opacity 1s ease-in-out;
}

.slide.active {
  opacity: 1;
}

/* Button */
.btn {
  display: inline-block;
  background: yellow;
  color: black;
  padding: 10px 20px;
  margin-top: 10px;
  text-decoration: none;
  font-weight: bold;
  border-radius: 5px;
}

/* Sections */
.section {
  padding: 50px 20px;
  text-align: center;
}

/* Grid Layout */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

/* Gallery */
.gallery img {
  width: 100%;
  height: 250px;
  object-fit: cover;
  border-radius: 10px;
  transition: transform 0.3s ease;
}

.gallery img:hover {
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .gallery img {
    height: 200px;
  }
}

/* Footer */
.footer {
  background: #333;
  color: white;
  text-align: center;
  padding: 15px;
  margin-top: 20px;
}

/* Responsive Adjustments */
@media (max-width: 600px) {
  .hero h1 {
    font-size: 24px;
  }

  .btn {
    padding: 8px 16px;
  }
}
</style>