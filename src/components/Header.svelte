<script lang="ts">
  import { onMount } from 'svelte';
  
  let isMenuOpen = false;
  let isScrolled = false;
  let currentPath = '';
  
  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }

  function handleScroll() {
    isScrolled = window.scrollY > 50;
  }

  onMount(() => {
    currentPath = window.location.pathname;
    window.addEventListener('scroll', handleScroll);
    
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });
</script>

<header class="header" class:header--scrolled={isScrolled}>
  <div class="header__container">
    <div class="header__logo">
      <a href="/" class="header__logo-link" aria-label="Home">
        <img 
          src="/practical-cleaning-company_2024-logo.svg" 
          alt="Practical Cleaning Company Logo" 
          class="header__logo-image"
          width="225" 
          height="125"
        >
      </a>
    </div>

    <button 
      class="header__menu-toggle" 
      aria-expanded={isMenuOpen} 
      aria-controls="primary-nav"
      aria-label="Toggle navigation menu"
      on:click={toggleMenu}
    >
      <i class="fas fa-bars" aria-hidden="true"></i>
    </button>

    <nav 
      id="primary-nav" 
      class="header__nav" 
      class:header__nav--active={isMenuOpen}  
      aria-label="Main navigation"
    >
      <ul class="header__nav-list">
        <li class="header__nav-item">
          <a 
            href="/contact" 
            class="header__nav-link"
            class:header__nav-link--active={currentPath === '/contact'}
            aria-current={currentPath === '/contact' ? 'page' : undefined}
          >
            <i class="fas fa-envelope header__nav-icon" aria-hidden="true"></i>
            <span class="header__nav-text">Contact</span>
          </a>
        </li>
        <li class="header__nav-item">
          <a 
            href="/services" 
            class="header__nav-link"
            class:header__nav-link--active={currentPath === '/services'}
            aria-current={currentPath === '/services' ? 'page' : undefined}
          >
            <i class="fas fa-broom header__nav-icon" aria-hidden="true"></i>
            <span class="header__nav-text">Services</span>
          </a>
        </li>
        <li class="header__nav-item">
          <a 
            href="/faq" 
            class="header__nav-link"
            class:header__nav-link--active={currentPath === '/faq'}
            aria-current={currentPath === '/faq' ? 'page' : undefined}
          >
            <i class="fas fa-question-circle header__nav-icon" aria-hidden="true"></i>
            <span class="header__nav-text">FAQ</span>
          </a>
        </li>
        <li class="header__nav-item">
          <a 
            href="/about" 
            class="header__nav-link"
            class:header__nav-link--active={currentPath === '/about'}
            aria-current={currentPath === '/about' ? 'page' : undefined}
          >
            <i class="fas fa-info-circle header__nav-icon" aria-hidden="true"></i>
            <span class="header__nav-text">About</span>
          </a>
        </li>
      </ul>
    </nav>
  </div>
</header>

<style lang="scss">
  .header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: #ffffff;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    z-index: 1000;

    &--scrolled {
      padding: 0.5rem 0;
      background-color: rgba(255, 255, 255, 0.95);
    }

    &__container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 1rem 1rem 1rem 1rem ;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    &__logo {
      &-image {
        max-width: 100%;
        height: auto;
      }
    }

    &__menu-toggle {
      display: none;
      background: none;
      border: none;
      font-size: 1.5rem;
      cursor: pointer;
      padding: 0.5rem;
      color: #333;

      &:hover {
        color: #007bff;
      }

      &:focus {
        outline: 2px solid #007bff;
        outline-offset: 2px;
      }
    }

    &__nav {
      &-list {
        display: flex;
        list-style: none;
        margin: 0;
        padding: 0;
        gap: 2rem;
      }

      &-item {
        display: flex;
        align-items: center;
      }

      &-link {
        color: #333;
        text-decoration: none;
        font-size: 1rem;
        display: flex;
        align-items: center;
        gap: 0.5rem;
        padding: 0.5rem;
        transition: color 0.3s ease;

        &:hover, &:focus {
          color: #007bff;
        }

        &--active {
          color: #007bff;
          font-weight: bold;
        }
      }

      &-icon {
        font-size: 1.1rem;
      }
    }
  }

  @media (max-width: 768px) {
    .header {
      &__menu-toggle {
        display: block;
      }

      &__nav {
        position: absolute;
        top: 100%;
        left: 0;
        width: 100%;
        background-color: #ffffff;
        padding: 1rem;
        transform: translateY(-100%);
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

        &--active {
          transform: translateY(0);
          opacity: 1;
          visibility: visible;
        }

        &-list {
          flex-direction: column;
          gap: 1rem;
        }

        &-item {
          width: 100%;
        }

        &-link {
          padding: 0.75rem;
          justify-content: center;

          &:hover {
            background-color: #f8f9fa;
          }
        }
      }
    }
  }
</style>