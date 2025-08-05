<script>
  import { onMount } from 'svelte';
  import Header from './lib/components/Header.svelte';
  import Footer from './lib/components/Footer.svelte';
  import Home from './lib/components/Home.svelte';
  import Accommodations from './lib/components/Accommodations.svelte';
  import Transport from './lib/components/Transport.svelte';
  import Tours from './lib/components/Tours.svelte';
  import Itinerary from './lib/components/Itinerary.svelte';
  import Contact from './lib/components/Contact.svelte';
  import Auth from './lib/components/Auth.svelte';
  import UserDashboard from './lib/components/UserDashboard.svelte';
  import BookingModal from './lib/components/BookingModal.svelte';

  // Router state
  let currentRoute = 'home';
  let previousRoute = '';
  let showAuth = false;
  let showBookingModal = false;
  let bookingType = '';
  let bookingItem = null;
  let isLoggedIn = false;
  let user = null;

  // Check if user is logged in from localStorage
  onMount(() => {
    const storedUser = localStorage.getItem('shiloh_user');
    if (storedUser) {
      try {
        user = JSON.parse(storedUser);
        isLoggedIn = true;
      } catch (e) {
        console.error('Failed to parse user data', e);
      }
    }
  });

  // Handle navigation
  function handleNavigation(event) {
    previousRoute = currentRoute;
    currentRoute = event.detail.route;
    window.scrollTo(0, 0);
  }

  // Auth handlers
  function showAuthModal() {
    showAuth = true;
  }

  function hideAuthModal() {
    showAuth = false;
  }

  function handleLogin(event) {
    user = event.detail.user;
    isLoggedIn = true;
    localStorage.setItem('shiloh_user', JSON.stringify(user));
    showAuth = false;
  }

  function handleLogout() {
    user = null;
    isLoggedIn = false;
    localStorage.removeItem('shiloh_user');
    if (currentRoute === 'dashboard') {
      currentRoute = 'home';
    }
  }

  // Booking handlers
  function openBookingModal(event) {
    bookingType = event.detail.type;
    bookingItem = event.detail.item;
    showBookingModal = true;
  }

  function closeBookingModal() {
    showBookingModal = false;
    bookingItem = null;
  }

  function handleBookingComplete() {
    showBookingModal = false;
    bookingItem = null;
    // Could add a success message or redirect to dashboard
  }
</script>

<div class="app">
  <Header 
    {currentRoute} 
    {isLoggedIn} 
    on:navigate={handleNavigation} 
    on:login={showAuthModal}
    on:logout={handleLogout}
  />

  <main>
    {#if currentRoute === 'home'}
      <Home on:navigate={handleNavigation} on:book={openBookingModal} />
    {:else if currentRoute === 'accommodations'}
      <Accommodations on:book={openBookingModal} />
    {:else if currentRoute === 'transport'}
      <Transport on:book={openBookingModal} />
    {:else if currentRoute === 'tours'}
      <Tours on:book={openBookingModal} />
    {:else if currentRoute === 'itinerary'}
      <Itinerary {isLoggedIn} on:login={showAuthModal} />
    {:else if currentRoute === 'contact'}
      <Contact />
    {:else if currentRoute === 'dashboard' && isLoggedIn}
      <UserDashboard {user} />
    {:else}
      <Home on:navigate={handleNavigation} on:book={openBookingModal} />
    {/if}
  </main>

  <Footer on:navigate={handleNavigation} />

  {#if showAuth}
    <Auth 
      on:close={hideAuthModal} 
      on:login={handleLogin}
    />
  {/if}

  {#if showBookingModal}
    <BookingModal 
      {bookingType} 
      {bookingItem} 
      {isLoggedIn} 
      {user}
      on:close={closeBookingModal} 
      on:login={showAuthModal}
      on:complete={handleBookingComplete} 
    />
  {/if}
</div>

<style>
  .app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  main {
    flex: 1;
  }

  :global(html, body) {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
  }

  :global(body) {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    overflow-x: hidden;
  }

  :global(*, *::before, *::after) {
    box-sizing: border-box;
  }

  :global(img) {
    max-width: 100%;
    height: auto;
  }

  :global(button, input, select, textarea) {
    font-family: inherit;
  }
</style>