<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useColorMode } from "@vueuse/core";
const mode = useColorMode();

interface Review {
  id: number;
  name: string;
  college: string;
  rating: number;
  image: string;
  review: string;
}

// First row reviews (scrolls left to right)
const firstRowReviews = ref<Review[]>([
  {
    id: 1,
    name: "Dr. Ananya Sharma",
    college: "AIIMS Delhi",
    rating: 5,
    image: "/reviews/student1.jpg",
    review: "PYQS.com has transformed my NEET PG preparation. The well-organized question bank helped me improve my weak subjects significantly."
  },
  {
    id: 2,
    name: "Dr. Rajesh Kumar",
    college: "King George's Medical University",
    rating: 5,
    image: "/reviews/student2.jpg",
    review: "The AI-powered analytics helped me focus on high-yield topics. I've seen a 30% improvement in my mock test scores in just 2 months!"
  },
  {
    id: 3,
    name: "Dr. Priya Patel",
    college: "Grant Medical College, Mumbai",
    rating: 4,
    image: "/reviews/student3.jpg",
    review: "The subject-wise categorization of previous questions made my revision strategy much more effective. Highly recommended!"
  },
  {
    id: 4,
    name: "Dr. Arjun Singh",
    college: "Maulana Azad Medical College",
    rating: 5,
    image: "/reviews/student4.jpg",
    review: "PYQS.com's adaptive learning system helped identify my knowledge gaps. The personalized study plan was exactly what I needed."
  },
  {
    id: 5,
    name: "Dr. Nisha Verma",
    college: "Seth G.S. Medical College",
    rating: 4,
    image: "/reviews/student5.jpg",
    review: "The detailed explanations for each question helped me understand concepts better. Now I approach MCQs with much more confidence."
  },
]);

// Second row reviews (scrolls right to left)
const secondRowReviews = ref<Review[]>([
  {
    id: 6,
    name: "Dr. Vikram Choudhary",
    college: "Christian Medical College, Vellore",
    rating: 5,
    image: "/reviews/student6.jpg",
    review: "The timed mock tests accurately simulate NEET PG exam conditions. My test-taking speed and accuracy have both improved dramatically."
  },
  {
    id: 7,
    name: "Dr. Meera Reddy",
    college: "Madras Medical College",
    rating: 4,
    image: "/reviews/student7.jpg",
    review: "PYQS.com's image-based questions are incredibly helpful for practicing visual diagnosis - a crucial skill for NEET PG."
  },
  {
    id: 8,
    name: "Dr. Karthik Nair",
    college: "Jawaharlal Institute of Postgraduate Medical Education & Research",
    rating: 5,
    image: "/reviews/student8.jpg",
    review: "The detailed performance analytics helped me understand my progress over time and adjust my preparation accordingly."
  },
  {
    id: 9,
    name: "Dr. Shreya Gupta",
    college: "Government Medical College, Chandigarh",
    rating: 5,
    image: "/reviews/student9.jpg",
    review: "The mobile app is perfect for on-the-go revision during hospital rotations. It's been my constant companion during internship."
  },
  {
    id: 10,
    name: "Dr. Aditya Malhotra",
    college: "R.G. Kar Medical College",
    rating: 4,
    image: "/reviews/student10.jpg",
    review: "The regular updates with new questions and explanations keep the content fresh and relevant to the changing exam pattern."
  },
]);

// Third row reviews (scrolls left to right)
const thirdRowReviews = ref<Review[]>([
  {
    id: 11,
    name: "Dr. Kavita Menon",
    college: "Stanley Medical College",
    rating: 5,
    image: "/reviews/student11.jpg",
    review: "The subject experts who create content for PYQS.com really understand what's important for NEET PG. Every minute spent on the platform is valuable."
  },
  {
    id: 12,
    name: "Dr. Rohit Desai",
    college: "B.J. Medical College, Ahmedabad",
    rating: 4,
    image: "/reviews/student12.jpg",
    review: "The discussion forum for each question helped me understand different perspectives and approaches to complex topics."
  },
  {
    id: 13,
    name: "Dr. Sanya Joshi",
    college: "Kasturba Medical College, Manipal",
    rating: 5,
    image: "/reviews/student13.jpg",
    review: "I appreciate the error reporting feature. The team quickly corrects any inaccuracies, ensuring we learn from correct information."
  },
  {
    id: 14,
    name: "Dr. Vivek Raghavan",
    college: "Government Medical College, Kozhikode",
    rating: 5,
    image: "/reviews/student14.jpg",
    review: "The difficulty-based filtering helped me gradually increase the challenge as my preparation improved. Perfect for progressive learning."
  },
  {
    id: 15,
    name: "Dr. Tanvi Deshmukh",
    college: "Armed Forces Medical College, Pune",
    rating: 4,
    image: "/reviews/student15.jpg",
    review: "The year-wise sorting of PYQs gave me insight into how exam patterns have evolved, helping me focus on what's most relevant now."
  },
]);

// Speed control for each row
const speed1 = ref(45); // seconds
const speed2 = ref(50); // seconds
const speed3 = ref(55); // seconds

// Duplicate reviews for seamless looping
onMounted(() => {
  firstRowReviews.value = [...firstRowReviews.value, ...firstRowReviews.value];
  secondRowReviews.value = [...secondRowReviews.value, ...secondRowReviews.value];
  thirdRowReviews.value = [...thirdRowReviews.value, ...thirdRowReviews.value];
});
</script>

<template>
  <section class="py-24 sm:py-32 overflow-hidden" id="reviews">
    <!-- Section header -->
    <div class="container text-center mb-16">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider animate-fade-in">
        Testimonials
      </h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold mb-4 gradient-text animate-slide-up">
        What Our Students Say
      </h2>

      <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8 animate-slide-up" style="animation-delay: 100ms;">
        Hear from medical students across India who have transformed their NEET PG preparation with PYQS.com
      </h3>
    </div>

    <!-- Reviews marquee container -->
    <div class="reviews-marquee-container">
      <!-- First row (left to right) -->
      <div class="marquee-row">
        <div class="marquee-track ltr" :style="{ animationDuration: `${speed1}s` }">
          <div class="marquee-content">
            <div v-for="(review, idx) in firstRowReviews" :key="review.id" 
                 class="review-card"
                 :class="`gradient-card-${idx % 5}`">
              <div class="review-header">
                <div class="avatar-and-info">
                  <div class="avatar-wrapper" :class="`gradient-${idx % 5}`">
                    <div class="avatar" :style="{ backgroundImage: `url(${review.image})` }"></div>
                  </div>
                  <div class="user-info">
                    <div class="name">{{ review.name }}</div>
                    <div class="college">{{ review.college }}</div>
                  </div>
                </div>
                <div class="rating">
                  <span v-for="i in 5" :key="i" class="star" :class="{ 'star-filled': i <= review.rating }">
                    ★
                  </span>
                </div>
              </div>
              <div class="review-content">
                "{{ review.review }}"
              </div>
              <div class="card-shine"></div>
            </div>
          </div>
        </div>
      </div>

      <!-- Second row (right to left) -->
      <div class="marquee-row">
        <div class="marquee-track rtl" :style="{ animationDuration: `${speed2}s` }">
          <div class="marquee-content">
            <div v-for="(review, idx) in secondRowReviews" :key="review.id" 
                 class="review-card"
                 :class="`gradient-card-${(idx + 2) % 5}`">
              <div class="review-header">
                <div class="avatar-and-info">
                  <div class="avatar-wrapper" :class="`gradient-${(idx + 2) % 5}`">
                    <div class="avatar" :style="{ backgroundImage: `url(${review.image})` }"></div>
                  </div>
                  <div class="user-info">
                    <div class="name">{{ review.name }}</div>
                    <div class="college">{{ review.college }}</div>
                  </div>
                </div>
                <div class="rating">
                  <span v-for="i in 5" :key="i" class="star" :class="{ 'star-filled': i <= review.rating }">
                    ★
                  </span>
                </div>
              </div>
              <div class="review-content">
                "{{ review.review }}"
              </div>
              <div class="card-shine"></div>
            </div>
          </div>
        </div>
      </div>

      <!-- Third row (left to right) -->
      <div class="marquee-row">
        <div class="marquee-track ltr" :style="{ animationDuration: `${speed3}s` }">
          <div class="marquee-content">
            <div v-for="(review, idx) in thirdRowReviews" :key="review.id" 
                 class="review-card"
                 :class="`gradient-card-${(idx + 4) % 5}`">
              <div class="review-header">
                <div class="avatar-and-info">
                  <div class="avatar-wrapper" :class="`gradient-${(idx + 4) % 5}`">
                    <div class="avatar" :style="{ backgroundImage: `url(${review.image})` }"></div>
                  </div>
                  <div class="user-info">
                    <div class="name">{{ review.name }}</div>
                    <div class="college">{{ review.college }}</div>
                  </div>
                </div>
                <div class="rating">
                  <span v-for="i in 5" :key="i" class="star" :class="{ 'star-filled': i <= review.rating }">
                    ★
                  </span>
                </div>
              </div>
              <div class="review-content">
                "{{ review.review }}"
              </div>
              <div class="card-shine"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Marquee container styling */
.reviews-marquee-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 2rem;
  overflow: hidden;
}

.marquee-row {
  width: 100%;
  overflow: hidden;
  position: relative;
}

.marquee-track {
  display: flex;
  width: fit-content;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

.marquee-track.ltr {
  animation-name: scroll-ltr;
}

.marquee-track.rtl {
  animation-name: scroll-rtl;
}

.marquee-content {
  display: flex;
  gap: 2rem;
  padding: 0.5rem;
}

/* Review card styling */
.review-card {
  width: 340px;
  background-color: hsl(var(--card));
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.06);
  transition: all 0.4s cubic-bezier(0.22, 1, 0.36, 1);
  display: flex;
  flex-direction: column;
  gap: 1rem;
  flex-shrink: 0;
  border: 1px solid rgba(140, 56, 234, 0.1);
  position: relative;
  overflow: hidden;
  transform-style: preserve-3d;
  perspective: 1000px;
}

.dark .review-card {
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  border: 1px solid rgba(140, 56, 234, 0.15);
}

/* Improved hover effect */
.review-card:hover {
  transform: translateY(-6px) scale(1.02) rotateX(2deg);
  box-shadow: 0 20px 30px rgba(140, 56, 234, 0.15), 0 10px 10px rgba(140, 56, 234, 0.05);
  z-index: 10;
}

/* Gradient-specific card styling */
.gradient-card-0:hover {
  border-color: rgba(140, 56, 234, 0.3);
}

.gradient-card-1:hover {
  border-color: rgba(57, 93, 235, 0.3);
}

.gradient-card-2:hover {
  border-color: rgba(76, 175, 80, 0.3);
}

.gradient-card-3:hover {
  border-color: rgba(233, 30, 99, 0.3);
}

.gradient-card-4:hover {
  border-color: rgba(255, 152, 0, 0.3);
}

/* Card shine effect */
.card-shine {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.05) 50%,
    rgba(255, 255, 255, 0) 100%
  );
  opacity: 0;
  z-index: 2;
  transition: all 0.5s ease;
  pointer-events: none;
}

.review-card:hover .card-shine {
  opacity: 1;
  transform: translateY(-100%) translateX(100%);
  transition: all 1s ease;
}

/* Avatar wrapper with gradient borders */
.avatar-wrapper {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  padding: 2px;
  background: linear-gradient(45deg, rgba(140, 56, 234, 0.8), rgba(92, 80, 235, 0.8));
  position: relative;
  z-index: 1;
  transition: all 0.3s ease;
}

.review-card:hover .avatar-wrapper {
  transform: scale(1.1);
}

/* Gradient variations for avatar wrappers */
.gradient-0 {
  background: linear-gradient(45deg, #8c38ea, #5c50eb);
}

.gradient-1 {
  background: linear-gradient(45deg, #395deb, #03a9f4);
}

.gradient-2 {
  background: linear-gradient(45deg, #4caf50, #8bc34a);
}

.gradient-3 {
  background: linear-gradient(45deg, #e91e63, #f06292);
}

.gradient-4 {
  background: linear-gradient(45deg, #ff9800, #ffb300);
}

/* Updated avatar style */
.avatar {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background-size: cover;
  background-position: center;
  border: 2px solid white;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.review-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.avatar-and-info {
  display: flex;
  gap: 0.75rem;
  align-items: center;
}

.user-info {
  display: flex;
  flex-direction: column;
}

.name {
  font-weight: 600;
  font-size: 0.9rem;
  color: hsl(var(--foreground));
}

.college {
  font-size: 0.75rem;
  color: hsl(var(--muted-foreground));
  line-height: 1.2;
  max-width: 160px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.rating {
  display: flex;
  gap: 1px;
}

.star {
  color: #ccc;
  font-size: 1rem;
}

.star-filled {
  color: #F9A825;
}

.review-content {
  font-size: 0.875rem;
  line-height: 1.5;
  color: hsl(var(--muted-foreground));
  font-style: italic;
}

/* Animation keyframes */
@keyframes scroll-ltr {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(calc(-50% - 1rem));
  }
}

@keyframes scroll-rtl {
  0% {
    transform: translateX(calc(-50% - 1rem));
  }
  100% {
    transform: translateX(0);
  }
}

/* Section header gradient text */
.gradient-text {
  background: linear-gradient(90deg, #8c38ea 0%, #5c50eb 50%, #395deb 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  display: inline-block;
}

/* Animations */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.animate-fade-in {
  opacity: 0;
  animation: fadeIn 0.6s ease-out forwards;
}

.animate-slide-up {
  opacity: 0;
  animation: slideUp 0.6s ease-out forwards;
}

/* Media queries for responsiveness */
@media (max-width: 768px) {
  .review-card {
    width: 280px;
    padding: 1.25rem;
  }
  
  .avatar-wrapper {
    width: 48px;
    height: 48px;
    padding: 2px;
  }
  
  .name {
    font-size: 0.8rem;
  }
  
  .college {
    font-size: 0.7rem;
    max-width: 120px;
  }
  
  .review-content {
    font-size: 0.8rem;
  }
}
</style>