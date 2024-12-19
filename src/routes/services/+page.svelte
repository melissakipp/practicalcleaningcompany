<script>
  import { onMount } from 'svelte';

  let isVisible = false;

  onMount(() => {
    isVisible = true;
  });
</script>

<div class="services" class:services--visible={isVisible}>
  <div class="services__hero">
    <h1 class="services__title">Our Services</h1>
    <p class="services__subtitle">Creating balanced and energy-efficient environments for your workspace</p>
  </div>

  <div class="services__container">
    <section class="services__section">
      <h2 class="services__section-title">
        <i class="fas fa-broom" aria-hidden="true"></i>
        Standard Cleaning Services
      </h2>
      <div class="services__content">
        <p>Our comprehensive standard cleaning package includes:</p>
        <ul class="services__list">
          <li>Thorough vacuuming of all floor surfaces</li>
          <li>Dusting of furniture and fixtures</li>
          <li>Trash removal and bin sanitization</li>
          <li>Complete restroom sanitization</li>
          <li>General floor cleaning and maintenance</li>
        </ul>
        <p>Perfect for routine maintenance to keep your workspace consistently clean and presentable.</p>
      </div>
    </section>

    <section class="services__section">
      <h2 class="services__section-title">
        <i class="fas fa-spray-can" aria-hidden="true"></i>
        Deep Cleaning Services
      </h2>
      <div class="services__content">
        <p>Our intensive deep cleaning service includes all standard cleaning plus:</p>
        <ul class="services__list">
          <li>Deep carpet cleaning and stain removal</li>
          <li>Window washing and frame cleaning</li>
          <li>Thorough cleaning of hard-to-reach areas</li>
          <li>Advanced sanitization processes</li>
          <li>Detailed surface treatment and restoration</li>
        </ul>
        <p>Ideal for seasonal refreshes or initial cleaning of new spaces.</p>
      </div>
    </section>

    <section class="services__section">
      <h2 class="services__section-title">
        <i class="fas fa-leaf" aria-hidden="true"></i>
        Atmosphere Curation
      </h2>
      <div class="services__content">
        <p>Enhance your workspace environment with our unique atmosphere curation services:</p>
        <ul class="services__list">
          <li>Natural, non-intrusive scent management</li>
          <li>Live office plants selection and maintenance</li>
          <li>High-efficiency air filtration systems</li>
          <li>Ambient environment optimization</li>
          <li>Workspace harmony assessment</li>
        </ul>
        <p>Transform your office into a harmonious and productive environment.</p>
      </div>
    </section>

    <section class="services__section">
      <h2 class="services__section-title">
        <i class="fas fa-clipboard-check" aria-hidden="true"></i>
        Custom Cleaning Plans
      </h2>
      <div class="services__content">
        <p>We understand that each business has unique needs. Our custom plans include:</p>
        <ul class="services__list">
          <li>Personalized cleaning schedule</li>
          <li>Industry-specific cleaning protocols</li>
          <li>Eco-friendly product selection</li>
          <li>Flexible service timing</li>
          <li>Specialized area treatment</li>
        </ul>
        <p>Contact us to create a cleaning plan tailored to your specific requirements.</p>
      </div>
    </section>
  </div>
</div>

<style lang="scss">
  .services {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.5s ease, transform 0.5s ease;

    &--visible {
      opacity: 1;
      transform: translateY(0);
    }

    &__hero {
      background-color: #f8f9fa;
      padding: 4rem 2rem;
      text-align: center;
      margin-bottom: 3rem;
    }

    &__title {
      color: #2c3e50;
      font-size: 2.5rem;
      margin-bottom: 1rem;
    }

    &__subtitle {
      color: #6c757d;
      font-size: 1.2rem;
      max-width: 600px;
      margin: 0 auto;
    }

    &__container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 1rem;
    }

    &__section {
      margin-bottom: 3rem;
      padding: 2rem;
      background-color: #fff;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s ease;

      &:hover {
        transform: translateY(-5px);
      }
    }

    &__section-title {
      color: #2c3e50;
      font-size: 1.8rem;
      margin-bottom: 1.5rem;
      display: flex;
      align-items: center;
      gap: 1rem;

      i {
        color: #3498db;
      }
    }

    &__content {
      color: #4a5568;
      font-size: 1.1rem;
      line-height: 1.6;
    }

    &__list {
      list-style: none;
      padding: 0;
      margin: 1.5rem 0;

      li {
        margin-bottom: 0.8rem;
        padding-left: 1.5rem;
        position: relative;

        &::before {
          content: "•";
          color: #3498db;
          position: absolute;
          left: 0;
          top: 0;
        }
      }
    }
  }

  // Responsive styles
  @media (max-width: 768px) {
    .services {
      &__hero {
        padding: 3rem 1rem;
      }

      &__title {
        font-size: 2rem;
      }

      &__subtitle {
        font-size: 1.1rem;
      }

      &__section-title {
        font-size: 1.5rem;
      }

      &__content {
        font-size: 1rem;
      }
    }
  }

  @media (max-width: 480px) {
    .services {
      &__hero {
        padding: 2rem 1rem;
      }

      &__title {
        font-size: 1.8rem;
      }

      &__section {
        padding: 1.5rem;
      }

      &__section-title {
        font-size: 1.3rem;
      }
    }
  }
</style>