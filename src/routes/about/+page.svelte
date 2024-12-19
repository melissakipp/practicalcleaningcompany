<script>
  import { onMount } from 'svelte';
  
  let isVisible = false;
  
  onMount(() => {
    isVisible = true;
  });
</script>

<style lang="scss">
  .about {
    &__container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 2rem;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.5s ease, transform 0.5s ease;
      
      &--visible {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    &__title {
      font-size: 2.5rem;
      color: var(--primary-color);
      margin-bottom: 2rem;
      text-align: center;
      
      @media (max-width: 768px) {
        font-size: 2rem;
      }
    }
    
    &__content {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 3rem;
      
      @media (max-width: 768px) {
        grid-template-columns: 1fr;
      }
    }
    
    &__text {
      font-size: 1.1rem;
      line-height: 1.6;
      
      &-section {
        margin-bottom: 2rem;
      }
    }
    
    &__highlight {
      background-color: var(--accent-color);
      padding: 2rem;
      border-radius: 8px;
      margin-top: 2rem;
      
      &-title {
        font-size: 1.5rem;
        margin-bottom: 1rem;
        display: flex;
        align-items: center;
        gap: 0.5rem;
      }
    }
    
    &__values {
      list-style: none;
      padding: 0;
      
      &-item {
        display: flex;
        align-items: center;
        gap: 1rem;
        margin-bottom: 1rem;
        
        i {
          color: var(--primary-color);
          font-size: 1.2rem;
        }
      }
    }
  }
</style>

<article class="about__container" class:about__container--visible={isVisible}>
  <h1 class="about__title">About Practical Cleaning Company</h1>
  
  <div class="about__content">
    <div class="about__text">
      <div class="about__text-section">
        <p>Founded in 2017, Practical Cleaning Company is committed to creating balanced and energetic environments that transform office spaces into zones of social engagement and personal improvement. Based in Mesa, Arizona, we prioritize a natural and mindful approach to ensure clean, harmonious workspaces that enhance both productivity and wellbeing for all users.</p>
      </div>
      
      <div class="about__text-section">
        <p>Our specialized cleaning services cater to small and medium-sized businesses, focusing on delivering top-notch commercial cleaning that goes beyond basic maintenance. We believe in creating spaces that not only look clean but feel invigorating and promote positive energy.</p>
      </div>
    </div>
    
    <div class="about__highlight">
      <h2 class="about__highlight-title">
        <i class="fas fa-star" aria-hidden="true"></i>
        Our Core Values
      </h2>
      
      <ul class="about__values">
        <li class="about__values-item">
          <i class="fas fa-leaf" aria-hidden="true"></i>
          <span>Commitment to eco-friendly cleaning solutions</span>
        </li>
        <li class="about__values-item">
          <i class="fas fa-hand-sparkles" aria-hidden="true"></i>
          <span>Excellence in service quality</span>
        </li>
        <li class="about__values-item">
          <i class="fas fa-users" aria-hidden="true"></i>
          <span>Focus on customer satisfaction</span>
        </li>
        <li class="about__values-item">
          <i class="fas fa-heart" aria-hidden="true"></i>
          <span>Creating positive work environments</span>
        </li>
        <li class="about__values-item">
          <i class="fas fa-sync-alt" aria-hidden="true"></i>
          <span>Continuous improvement and innovation</span>
        </li>
      </ul>
    </div>
  </div>
</article>