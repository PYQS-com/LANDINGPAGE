<script setup lang="ts">
import { Mail } from "lucide-vue-next";
</script>

<template>
  <section
    id="contact"
    class="container py-24 sm:py-32"
  >
    <div class="text-center max-w-2xl mx-auto">
      <div class="mb-8">
        <h2 class="text-lg text-primary text-center mb-2 tracking-wider animate-fade-in">Contact</h2>
        <h2 class="text-3xl md:text-4xl text-center font-bold mb-4 gradient-text animate-slide-up">Get In Touch</h2>
        <h3 class="md:w-3/4 mx-auto text-xl text-center text-muted-foreground mb-8 animate-slide-up" style="animation-delay: 100ms;">
          We'd love to hear from you. Send us a message and we'll respond as soon as possible.
        </h3>
      </div>
      
      <div class="contact-email-container animate-fade-in" style="animation-delay: 200ms;">
        <div class="flex items-center justify-center gap-4 mb-2">
          <div class="email-icon-container">
            <Mail class="email-icon" />
          </div>
          <div class="text-left">
            <div class="font-bold text-lg mb-1 text-foreground">Email us</div>
            <a 
              href="mailto:hello@pyqs.com" 
              class="email-link text-xl font-medium"
            >
              hello@pyqs.com
            </a>
          </div>
        </div>
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

.contact-email-container {
  padding: 2rem;
  border-radius: 16px;
  background: hsl(var(--card));
  border: 1px solid hsl(var(--border));
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
}

.dark .contact-email-container {
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.contact-email-container:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.dark .contact-email-container:hover {
  box-shadow: 0 8px 25px rgba(255, 255, 255, 0.05);
}

.email-icon-container {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, #1a1a1a, #2d2d2d);
  border-radius: 50%;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
}

.dark .email-icon-container {
  background: linear-gradient(135deg, #ffffff, #f0f0f0);
  box-shadow: 0 4px 15px rgba(255, 255, 255, 0.1);
}

.email-icon {
  width: 28px;
  height: 28px;
  color: white;
}

.dark .email-icon {
  color: #1a1a1a;
}

.email-icon-container:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

.dark .email-icon-container:hover {
  box-shadow: 0 6px 20px rgba(255, 255, 255, 0.2);
}

.email-link {
  color: #1a1a1a;
  text-decoration: none;
  transition: all 0.3s ease;
  font-weight: 600;
}

.dark .email-link {
  color: #ffffff;
}

.email-link:hover {
  color: #2d2d2d;
  text-decoration: underline;
}

.dark .email-link:hover {
  color: #f0f0f0;
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
  .contact-email-container {
    padding: 1.5rem;
  }
  
  .email-icon-container {
    width: 50px;
    height: 50px;
  }
  
  .email-icon {
    width: 24px;
    height: 24px;
  }
  
  .gradient-text {
    font-size: 2rem;
  }
}
</style>
