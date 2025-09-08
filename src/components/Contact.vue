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
        <h2 class="text-lg text-primary mb-2 tracking-wider">Contact</h2>
        <h2 class="text-3xl md:text-4xl font-bold mb-8">Get In Touch</h2>
      </div>
      
      <div class="contact-email-container">
        <div class="flex items-center justify-center gap-3 mb-4">
          <div class="email-icon-container">
            <Mail class="email-icon" />
          </div>
          <div>
            <div class="font-bold text-lg mb-1">Email us</div>
            <a 
              href="mailto:hello@pyqs.com" 
              class="email-link text-xl font-medium"
            >
              hello@pyqs.com
            </a>
          </div>
        </div>
        <p class="text-muted-foreground">
          We'd love to hear from you. Send us a message and we'll respond as soon as possible.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-email-container {
  padding: 2rem;
  border-radius: 16px;
  background: rgba(140, 56, 234, 0.05);
  border: 1px solid rgba(140, 56, 234, 0.1);
  transition: all 0.3s ease;
}

.dark .contact-email-container {
  background: rgba(140, 56, 234, 0.1);
  border: 1px solid rgba(140, 56, 234, 0.2);
}

.contact-email-container:hover {
  background: rgba(140, 56, 234, 0.08);
  border-color: rgba(140, 56, 234, 0.2);
  transform: translateY(-2px);
}

.dark .contact-email-container:hover {
  background: rgba(140, 56, 234, 0.15);
  border-color: rgba(140, 56, 234, 0.3);
}

.email-icon-container {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, #8c38ea, #5c50eb);
  border-radius: 50%;
  box-shadow: 0 4px 15px rgba(140, 56, 234, 0.3);
  transition: all 0.3s ease;
}

.email-icon {
  width: 28px;
  height: 28px;
  color: white;
}

.email-icon-container:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(140, 56, 234, 0.4);
}

.email-link {
  color: hsl(var(--primary));
  text-decoration: none;
  transition: all 0.3s ease;
}

.email-link:hover {
  color: rgba(140, 56, 234, 0.8);
  text-decoration: underline;
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
}
</style>
