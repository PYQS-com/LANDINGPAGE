<script setup lang="ts">
import { Mail } from "lucide-vue-next";
</script>

<template>
  <section
    id="contact"
    class="container py-16 sm:py-20"
  >
    <div class="text-center max-w-2xl mx-auto">
      <div class="mb-8">
        <h2 class="text-lg text-primary text-center mb-2 tracking-wider animate-fade-in">Contact</h2>
        <h2 class="text-3xl md:text-4xl text-center font-bold mb-4 gradient-text animate-slide-up">Get In Touch</h2>
        <h3 class="md:w-3/4 mx-auto text-xl text-center text-muted-foreground mb-8 animate-slide-up" style="animation-delay: 100ms;">
          We'd love to hear from you. Send us a message and we'll respond as soon as possible.
        </h3>
      </div>
      
      <div class="email-container animate-fade-in" style="animation-delay: 200ms;">
        <Mail class="email-icon" />
        <a href="mailto:hello@pyqs.in" class="email-link">
          hello@pyqs.in
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Gradient text styling for Contact section */
.gradient-text {
  background: linear-gradient(90deg, #1a1a1a 0%, #2d2d2d 50%, #1a1a1a 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  display: inline-block;
  text-shadow: 0 0 1px rgba(0, 0, 0, 0.05);
}

.dark .gradient-text {
  background: linear-gradient(90deg, #ffffff 0%, #f0f0f0 50%, #ffffff 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
}

.email-container {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  padding: 16px 24px;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 20px;
  transition: all 0.3s ease;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.dark .email-container {
  background: rgba(0, 0, 0, 0.5);
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 1px 3px rgba(255, 255, 255, 0.1);
}

.email-container:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  border-color: rgba(0, 0, 0, 0.2);
}

.dark .email-container:hover {
  box-shadow: 0 4px 12px rgba(255, 255, 255, 0.1);
  border-color: rgba(255, 255, 255, 0.2);
}

.email-icon {
  width: 20px;
  height: 20px;
  color: #666;
  transition: color 0.3s ease;
}

.dark .email-icon {
  color: #999;
}

.email-link {
  color: #333;
  text-decoration: none;
  font-size: 16px;
  font-weight: 500;
  letter-spacing: -0.01em;
  transition: color 0.3s ease;
}

.dark .email-link {
  color: #e5e5e7;
}

.email-container:hover .email-link {
  color: #007aff;
}

.dark .email-container:hover .email-link {
  color: #0a84ff;
}

.email-container:hover .email-icon {
  color: #007aff;
}

.dark .email-container:hover .email-icon {
  color: #0a84ff;
}

/* Animation keyframes */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Animation classes */
.animate-fade-in {
  opacity: 0;
  animation: fadeIn 0.8s ease-out forwards;
}

.animate-slide-up {
  opacity: 0;
  animation: slideUp 0.8s ease-out forwards;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .email-container {
    padding: 12px 20px;
  }
  
  .email-link {
    font-size: 15px;
  }
  
  .gradient-text {
    font-size: 2rem;
  }
}
</style>
