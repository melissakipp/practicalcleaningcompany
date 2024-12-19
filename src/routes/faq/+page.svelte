<script lang="ts">
  import { onMount } from 'svelte';

  interface FAQ {
    id: number;
    question: string;
    answer: string;
    isOpen: boolean;
  }

  let faqs: FAQ[] = [
    {
      id: 1,
      question: "What eco-friendly cleaning products do you use?",
      answer: "We exclusively use environmentally safe and sustainable cleaning products that are biodegradable and non-toxic. Our cleaning solutions are carefully selected to ensure they're effective while being gentle on both the environment and the health of your workspace occupants. This approach aligns with our commitment to creating clean, harmonious environments without compromising on sustainability.",
      isOpen: false
    },
    {
      id: 2,
      question: "What are your pricing tiers for commercial cleaning services?",
      answer: "We offer three main service tiers: Basic Tier ($75-$100 per visit) for spaces up to 1,000 sq. ft., Standard Tier ($100-$250 per visit) for spaces 1,000-3,000 sq. ft., and Premium Tier ($250-$400 per visit) for spaces over 3,000 sq. ft. Each tier includes customized cleaning solutions tailored to your specific needs. Final pricing depends on factors such as frequency of service, specific requirements, and additional services requested.",
      isOpen: false
    },
    {
      id: 3,
      question: "What sets your cleaning services apart from other companies?",
      answer: "Practical Cleaning Company specializes in creating balanced and energizing environments through our unique approach to commercial cleaning. We offer atmosphere curation services, including natural scent management and air quality improvement, alongside our eco-friendly cleaning practices. Our staff is professionally trained not only in cleaning techniques but also in customer service, ensuring a superior experience that enhances both the cleanliness and overall ambiance of your workspace.",
      isOpen: false
    },
    {
      id: 4,
      question: "What is included in your standard cleaning service?",
      answer: "Our standard cleaning service includes comprehensive care for your workspace: vacuuming, dusting, trash removal, restroom sanitization, floor cleaning, and basic kitchen/break room maintenance. We use eco-friendly products and focus on creating a harmonious environment. For businesses needing more intensive cleaning, we also offer deep cleaning services that include carpet cleaning, window washing, and specialized sanitation processes.",
      isOpen: false
    },
    {
      id: 5,
      question: "How do you ensure quality and consistency in your cleaning services?",
      answer: "We maintain high standards through our comprehensive quality assurance process. This includes regular staff training in eco-friendly cleaning techniques, detailed cleaning checklists for each service, post-service quality checks, and an active feedback system. We also provide a satisfaction guarantee and will promptly address any concerns to ensure our service meets your expectations.",
      isOpen: false
    }
  ];

  function toggleFAQ(id: number): void {
    faqs = faqs.map(faq => ({
      ...faq,
      isOpen: faq.id === id ? !faq.isOpen : false
    }));
  }

  onMount(() => {
    // Add keyboard navigation
    const accordions = document.querySelectorAll<HTMLElement>('.faq__item');
    accordions.forEach(accordion => {
      if (accordion) {
        accordion.addEventListener('keypress', (e: KeyboardEvent) => {
          if (e.key === 'Enter' || e.key === ' ') {
            e.preventDefault();
            const questionButton = accordion.querySelector<HTMLElement>('.faq__question');
            questionButton?.click();
          }
        });
      }
    });
  });
</script>

<style lang="scss">
  .faq {
    &__container {
      max-width: 800px;
      margin: 2rem auto;
      padding: 0 1rem;
    }

    &__title {
      color: #333;
      text-align: center;
      margin-bottom: 2rem;
      font-size: 2rem;
    }

    &__list {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    &__item {
      margin-bottom: 1rem;
      border: 1px solid #e0e0e0;
      border-radius: 8px;
      overflow: hidden;
      transition: all 0.3s ease;

      &:hover {
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      }

      &--active {
        border-color: #4a90e2;
      }
    }

    &__question {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;
      padding: 1rem;
      background-color: #f8f8f8;
      cursor: pointer;
      font-weight: 600;
      color: #333;
      border: none;
      text-align: left;
      transition: background-color 0.3s ease;

      &:hover {
        background-color: #f0f0f0;
      }

      &:focus {
        outline: 2px solid #4a90e2;
        outline-offset: -2px;
      }
    }

    &__icon {
      transition: transform 0.3s ease;
      margin-left: 1rem;
      font-size: 0.875rem;
      color: #666;

      &--open {
        transform: rotate(180deg);
      }
    }

    &__answer {
      padding: 0;
      max-height: 0;
      overflow: hidden;
      transition: all 0.3s ease;
      background-color: #fff;

      &--open {
        padding: 1rem;
        max-height: 500px;
      }

      p {
        margin: 0;
        line-height: 1.6;
      }
    }
  }

  // Responsive Design
  @media (max-width: 768px) {
    .faq {
      &__container {
        margin: 1rem;
      }

      &__title {
        font-size: 1.5rem;
      }

      &__question {
        font-size: 0.9rem;
        padding: 0.8rem;
      }

      &__answer {
        font-size: 0.9rem;

        &--open {
          padding: 0.8rem;
        }
      }
    }
  }
</style>

<div class="faq__container">
  <h1 class="faq__title">Frequently Asked Questions</h1>
  <ul class="faq__list" role="list">
    {#each faqs as faq (faq.id)}
      <li class="faq__item {faq.isOpen ? 'faq__item--active' : ''}">
        <button 
          class="faq__question"
          on:click={() => toggleFAQ(faq.id)}
          aria-expanded={faq.isOpen}
          aria-controls="faq-answer-{faq.id}"
        >
          <span>{faq.question}</span>
          <i 
            class="fas fa-chevron-down faq__icon {faq.isOpen ? 'faq__icon--open' : ''}" 
            aria-hidden="true"
          ></i>
        </button>
        <div 
          id="faq-answer-{faq.id}"
          class="faq__answer {faq.isOpen ? 'faq__answer--open' : ''}"
          role="region"
          aria-labelledby="faq-question-{faq.id}"
        >
          <p>{faq.answer}</p>
        </div>
      </li>
    {/each}
  </ul>
</div>