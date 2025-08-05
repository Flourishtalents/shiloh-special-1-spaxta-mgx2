<script>
  import { createEventDispatcher } from 'svelte';
  
  export let currentRoute = 'home';
  export let isLoggedIn = false;
  
  const dispatch = createEventDispatcher();
  let isMobileMenuOpen = false;
  
  function navigate(route) {
    dispatch('navigate', { route });
    isMobileMenuOpen = false;
  }
  
  function handleLogin() {
    dispatch('login');
  }
  
  function handleLogout() {
    dispatch('logout');
  }
  
  function toggleMobileMenu() {
    isMobileMenuOpen = !isMobileMenuOpen;
  }
</script>

<header class="bg-white shadow-md fixed w-full top-0 z-50">
  <div class="container-custom py-4 flex justify-between items-center">
    <!-- Logo -->
    <div class="flex items-center">
      <a href="#" on:click|preventDefault={() => navigate('home')} class="flex items-center">
        <img src="images/logo.png" alt="Shiloh Special" class="h-12 w-auto mr-2" />
        <span class="text-2xl font-bold text-primary">Shiloh Special</span>
      </a>
    </div>
    
    <!-- Desktop Navigation -->
    <nav class="hidden md:flex space-x-6">
      <a 
        href="#" 
        class="nav-link {currentRoute === 'home' ? 'active' : ''}" 
        on:click|preventDefault={() => navigate('home')}
      >
        Home
      </a>
      <a 
        href="#" 
        class="nav-link {currentRoute === 'accommodations' ? 'active' : ''}" 
        on:click|preventDefault={() => navigate('accommodations')}
      >
        Accommodations
      </a>
      <a 
        href="#" 
        class="nav-link {currentRoute === 'transport' ? 'active' : ''}" 
        on:click|preventDefault={() => navigate('transport')}
      >
        Car Rental
      </a>
      <a 
        href="#" 
        class="nav-link {currentRoute === 'tours' ? 'active' : ''}" 
        on:click|preventDefault={() => navigate('tours')}
      >
        Tours & Safaris
      </a>
      <a 
        href="#" 
        class="nav-link {currentRoute === 'itinerary' ? 'active' : ''}" 
        on:click|preventDefault={() => navigate('itinerary')}
      >
        Plan Itinerary
      </a>
      <a 
        href="#" 
        class="nav-link {currentRoute === 'contact' ? 'active' : ''}" 
        on:click|preventDefault={() => navigate('contact')}
      >
        Contact
      </a>
    </nav>
    
    <!-- Auth Buttons -->
    <div class="hidden md:flex items-center space-x-4">
      {#if isLoggedIn}
        <button 
          class="flex items-center text-sm font-medium text-primary hover:text-primary-dark"
          on:click|preventDefault={() => navigate('dashboard')}
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-1" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd" />
          </svg>
          My Account
        </button>
        <button 
          class="btn-secondary py-2 px-4 text-sm"
          on:click={handleLogout}
        >
          Logout
        </button>
      {:else}
        <button 
          class="btn-primary py-2 px-4 text-sm"
          on:click={handleLogin}
        >
          Sign In
        </button>
      {/if}
    </div>
    
    <!-- Mobile Menu Button -->
    <button 
      class="md:hidden text-primary focus:outline-none" 
      on:click={toggleMobileMenu}
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        {#if isMobileMenuOpen}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        {:else}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        {/if}
      </svg>
    </button>
  </div>
  
  <!-- Mobile Menu -->
  {#if isMobileMenuOpen}
    <div class="md:hidden bg-white pb-4 animate-fade-in">
      <nav class="flex flex-col space-y-3 px-4">
        <a 
          href="#" 
          class="nav-link-mobile {currentRoute === 'home' ? 'active' : ''}" 
          on:click|preventDefault={() => navigate('home')}
        >
          Home
        </a>
        <a 
          href="#" 
          class="nav-link-mobile {currentRoute === 'accommodations' ? 'active' : ''}" 
          on:click|preventDefault={() => navigate('accommodations')}
        >
          Accommodations
        </a>
        <a 
          href="#" 
          class="nav-link-mobile {currentRoute === 'transport' ? 'active' : ''}" 
          on:click|preventDefault={() => navigate('transport')}
        >
          Car Rental
        </a>
        <a 
          href="#" 
          class="nav-link-mobile {currentRoute === 'tours' ? 'active' : ''}" 
          on:click|preventDefault={() => navigate('tours')}
        >
          Tours & Safaris
        </a>
        <a 
          href="#" 
          class="nav-link-mobile {currentRoute === 'itinerary' ? 'active' : ''}" 
          on:click|preventDefault={() => navigate('itinerary')}
        >
          Plan Itinerary
        </a>
        <a 
          href="#" 
          class="nav-link-mobile {currentRoute === 'contact' ? 'active' : ''}" 
          on:click|preventDefault={() => navigate('contact')}
        >
          Contact
        </a>
        
        <div class="pt-2 border-t border-gray-200">
          {#if isLoggedIn}
            <a 
              href="#" 
              class="block py-2 text-primary hover:text-primary-dark" 
              on:click|preventDefault={() => navigate('dashboard')}
            >
              My Account
            </a>
            <button 
              class="w-full btn-secondary mt-2 py-2"
              on:click={handleLogout}
            >
              Logout
            </button>
          {:else}
            <button 
              class="w-full btn-primary py-2"
              on:click={handleLogin}
            >
              Sign In
            </button>
          {/if}
        </div>
      </nav>
    </div>
  {/if}
</header>

<!-- Spacer for fixed header -->
<div class="h-[72px]"></div>

<style>
  .nav-link {
    position: relative;
    color: var(--color-gray-600);
    font-weight: 500;
    padding: 0.25rem 0;
    transition: color 200ms ease;
  }
  
  .nav-link:hover {
    color: var(--color-primary);
  }
  
  .nav-link.active {
    color: var(--color-primary);
    font-weight: 600;
  }
  
  .nav-link.active::after {
    content: "";
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 100%;
    height: 2px;
    background-color: var(--color-primary);
  }
  
  .nav-link-mobile {
    padding: 0.75rem 0;
    font-weight: 500;
    color: var(--color-gray-600);
    border-bottom: 1px solid var(--color-gray-100);
  }
  
  .nav-link-mobile.active {
    color: var(--color-primary);
    font-weight: 600;
  }
</style>