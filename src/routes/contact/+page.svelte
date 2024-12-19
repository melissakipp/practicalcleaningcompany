<script lang="ts">
  import { onMount } from 'svelte';
  
  let isFormSubmitted = false;
  let formData = {
    name: '',
    email: '',
    phone: '',
    message: '',
    business: ''
  };

  const handleSubmit = (e: Event) => {
    e.preventDefault();
    isFormSubmitted = true;
    setTimeout(() => {
      isFormSubmitted = false;
      formData = {
        name: '',
        email: '',
        phone: '',
        message: '',
        business: ''
      };
    }, 3000);
  };

  onMount(() => {
    const script = document.createElement('script');
    script.src = 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/js/all.min.js';
    document.head.appendChild(script);
  });
</script>

<style lang="scss">
  .contact {
    &__container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 2rem;
    }

    &__header {
      text-align: center;
      margin-bottom: 3rem;
    }

    &__story {
      background-color: #f5f5f5;
      padding: 2rem;
      border-radius: 8px;
      margin-bottom: 3rem;

      &-title {
        color: #2c5282;
        margin-bottom: 1rem;
      }
    }

    &__form {
      max-width: 600px;
      margin: 0 auto;

      &-group {
        margin-bottom: 1.5rem;
      }

      &-label {
        display: block;
        margin-bottom: 0.5rem;
        color: #4a5568;
      }

      &-input,
      &-textarea {
        width: 100%;
        padding: 0.75rem;
        border: 1px solid #e2e8f0;
        border-radius: 4px;
        transition: border-color 0.2s;

        &:focus {
          outline: none;
          border-color: #2c5282;
        }
      }

      &-textarea {
        min-height: 150px;
        resize: vertical;
      }

      &-button {
        background-color: #2c5282;
        color: white;
        padding: 1rem 2rem;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        transition: background-color 0.2s;

        &:hover {
          background-color: #2a4365;
        }

        &:focus {
          outline: 2px solid #2c5282;
          outline-offset: 2px;
        }
      }
    }

    &__info {
      margin-top: 3rem;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      text-align: center;

      &-item {
        padding: 1rem;

        i {
          font-size: 1.5rem;
          color: #2c5282;
          margin-bottom: 1rem;
        }
      }
    }
  }

  .success-message {
    background-color: #48bb78;
    color: white;
    padding: 1rem;
    border-radius: 4px;
    text-align: center;
    margin-bottom: 1rem;
  }

  @media (max-width: 768px) {
    .contact {
      &__container {
        padding: 1rem;
      }

      &__info {
        grid-template-columns: 1fr;
      }
    }
  }
</style>

<div class="contact__container">
  <header class="contact__header">
    <h1>Contact Practical Cleaning</h1>
  </header>

  <section class="contact__story">
    <h2 class="contact__story-title">Creating Harmonious Workspaces Together</h2>
    <p>Since 2017, we've been dedicated to transforming office spaces into zones of social engagement and personal improvement. Our natural and mindful approach ensures clean, harmonious workspaces that enhance both productivity and wellbeing for all users. Located in the heart of Mesa, Arizona, we're here to help your business thrive through our eco-friendly cleaning solutions.</p>
  </section>

  {#if isFormSubmitted}
    <div class="success-message" role="alert">
      Thank you for reaching out! We'll get back to you within 24 hours.
    </div>
  {/if}

  <form class="contact__form" on:submit={handleSubmit}>
    <div class="contact__form-group">
      <label class="contact__form-label" for="name">Name *</label>
      <input 
        type="text" 
        id="name" 
        class="contact__form-input" 
        required 
        bind:value={formData.name}
        aria-required="true"
      >
    </div>

    <div class="contact__form-group">
      <label class="contact__form-label" for="business">Business Name *</label>
      <input 
        type="text" 
        id="business" 
        class="contact__form-input" 
        required 
        bind:value={formData.business}
        aria-required="true"
      >
    </div>

    <div class="contact__form-group">
      <label class="contact__form-label" for="email">Email *</label>
      <input 
        type="email" 
        id="email" 
        class="contact__form-input" 
        required 
        bind:value={formData.email}
        aria-required="true"
      >
    </div>

    <div class="contact__form-group">
      <label class="contact__form-label" for="phone">Phone</label>
      <input 
        type="tel" 
        id="phone" 
        class="contact__form-input" 
        bind:value={formData.phone}
      >
    </div>

    <div class="contact__form-group">
      <label class="contact__form-label" for="message">Message *</label>
      <textarea 
        id="message" 
        class="contact__form-textarea" 
        required 
        bind:value={formData.message}
        aria-required="true"
      ></textarea>
    </div>

    <button type="submit" class="contact__form-button">
      Send Message
    </button>
  </form>

  <div class="contact__info">
    <div class="contact__info-item">
      <i class="fas fa-map-marker-alt" aria-hidden="true"></i>
      <h3>Location</h3>
      <p>137 E Elliot Rd, Gilbert, AZ 85234</p>
    </div>

    <div class="contact__info-item">
      <i class="fas fa-phone" aria-hidden="true"></i>
      <h3>Phone</h3>
      <p>Contact: Melissa Kipp</p>
    </div>

    <div class="contact__info-item">
      <i class="fas fa-envelope" aria-hidden="true"></i>
      <h3>Connect With Us</h3>
      <p>
        <a href="https://www.facebook.com/PracticalCleaning2017/" aria-label="Visit our Facebook page">
          <i class="fab fa-facebook" aria-hidden="true"></i>
        </a>
        <a href="https://www.linkedin.com/company/practical-cleaning" aria-label="Visit our LinkedIn page">
          <i class="fab fa-linkedin" aria-hidden="true"></i>
        </a>
      </p>
    </div>
  </div>
</div>