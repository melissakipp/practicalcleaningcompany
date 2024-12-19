<script>
  import { onMount } from 'svelte';
  
  // Get current year for copyright
  const currentYear = new Date().getFullYear();
  
  // Social media links from business plan
  const socialLinks = [
    {
      url: 'https://www.facebook.com/PracticalCleaning2017/',
      icon: 'fa-facebook-f',
      label: 'Follow us on Facebook'
    },
    {
      url: 'https://www.linkedin.com/company/practical-cleaning',
      icon: 'fa-linkedin-in', 
      label: 'Connect with us on LinkedIn'
    }
  ];

  onMount(() => {
    // Load Font Awesome
    const script = document.createElement('script');
    script.src = 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/js/all.min.js';
    script.crossOrigin = 'anonymous';
    document.head.appendChild(script);
  });
</script>

<footer class="footer">
  <div class="footer__container">
    <div class="footer__content">
      <div class="footer__section">
        <h2>Contact Us</h2>
        <address>
          <p>137 E Elliot Rd</p>
          <p>Gilbert, AZ 85234</p>
          <p>(PO Box)</p>
          <p>
            <a href="mailto:contact@practicalcleaningcompany.com" class="footer__link">
              <i class="fas fa-envelope" aria-hidden="true"></i>
              <span>Email Us</span>
            </a>
          </p>
        </address>
      </div>

      <div class="footer__section">
        <h2>Quick Links</h2>
        <nav aria-label="Footer Navigation">
          <ul class="footer__links">
            <li><a href="/services">Our Services</a></li>
            <li><a href="/about">About Us</a></li>
            <li><a href="/contact">Contact</a></li>
            <li><a href="/quote">Get a Quote</a></li>
          </ul>
        </nav>
      </div>

      <div class="footer__section">
        <h2>Connect With Us</h2>
        <ul class="footer__social">
          {#each socialLinks as {url, icon, label}}
            <li>
              <a 
                href={url}
                class="footer__social-link"
                target="_blank"
                rel="noopener noreferrer"
                aria-label={label}
              >
                <i class={`fab ${icon}`} aria-hidden="true"></i>
              </a>
            </li>
          {/each}
        </ul>
      </div>
    </div>

    <div class="footer__bottom">
      <p>&copy; {currentYear} Practical Cleaning Company. All rights reserved.</p>
      <p class="footer__eco">
        <i class="fas fa-leaf" aria-hidden="true"></i>
        Committed to eco-friendly cleaning solutions
      </p>
    </div>
  </div>
</footer>

<style lang="scss">
  .footer {
    background-color: #1a374d;
    color: #ffffff;
    padding: 3rem 0;
    margin-top: auto;

    &__container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 1rem;
    }

    &__content {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      margin-bottom: 2rem;
    }

    &__section {
      h2 {
        font-size: 1.25rem;
        margin-bottom: 1rem;
        color: #b4e0e8;
      }
    }

    &__links {
      list-style: none;
      padding: 0;
      margin: 0;

      li {
        margin-bottom: 0.5rem;
      }

      a {
        color: #ffffff;
        text-decoration: none;
        transition: color 0.3s ease;

        &:hover, &:focus {
          color: #b4e0e8;
          text-decoration: underline;
        }
      }
    }

    &__social {
      list-style: none;
      padding: 0;
      margin: 0;
      display: flex;
      gap: 1rem;

      &-link {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 40px;
        height: 40px;
        background-color: rgba(255, 255, 255, 0.1);
        border-radius: 50%;
        color: #ffffff;
        transition: all 0.3s ease;

        &:hover, &:focus {
          background-color: #b4e0e8;
          color: #1a374d;
          transform: translateY(-2px);
        }
      }
    }

    &__bottom {
      text-align: center;
      padding-top: 2rem;
      border-top: 1px solid rgba(255, 255, 255, 0.1);

      p {
        margin: 0.5rem 0;
        font-size: 0.875rem;
      }
    }

    &__eco {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      color: #b4e0e8;
    }

    address {
      font-style: normal;
      line-height: 1.5;

      p {
        margin: 0.25rem 0;
      }
    }

    &__link {
      color: #ffffff;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      transition: color 0.3s ease;

      &:hover, &:focus {
        color: #b4e0e8;
        text-decoration: underline;
      }
    }

    @media (max-width: 768px) {
      padding: 2rem 0;

      &__content {
        grid-template-columns: 1fr;
        text-align: center;
      }

      &__social {
        justify-content: center;
      }

      address {
        text-align: center;
      }
    }

    @media (prefers-reduced-motion: reduce) {
      &__social-link {
        transition: none;
        transform: none;

        &:hover, &:focus {
          transform: none;
        }
      }
    }
  }
</style>