<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  // Featured accommodations
  const featuredAccommodations = [
    {
      id: 1,
      name: "Serena Hotel Kampala",
      location: "Kampala",
      price: "$180",
      rating: 4.8,
      image: "images/serena-hotel.jpg",
      description: "Experience luxury in the heart of Kampala with stunning city views.",
    },
    {
      id: 2,
      name: "Murchison Falls Lodge",
      location: "Murchison Falls National Park",
      price: "$210",
      rating: 4.9,
      image: "images/murchison-lodge.jpg",
      description: "Immerse yourself in nature with this premium safari lodge experience.",
    },
    {
      id: 3,
      name: "Lake Victoria Resort",
      location: "Entebbe",
      price: "$150",
      rating: 4.7,
      image: "images/lake-victoria-resort.jpg",
      description: "Beachfront resort with breathtaking views of Lake Victoria.",
    }
  ];

  // Featured tours
  const featuredTours = [
    {
      id: 1,
      name: "Gorilla Trekking Adventure",
      location: "Bwindi Impenetrable Forest",
      duration: "3 days",
      price: "$800",
      rating: 5.0,
      image: "images/gorilla-trekking.jpg",
      description: "Get up close with mountain gorillas in their natural habitat.",
    },
    {
      id: 2,
      name: "Big Five Safari",
      location: "Queen Elizabeth National Park",
      duration: "4 days",
      price: "$650",
      rating: 4.8,
      image: "/images/Safari.jpg",
      description: "Spot lions, elephants, buffalos, leopards, and rhinos on this safari adventure.",
    },
    {
      id: 3,
      name: "Nile River Expedition",
      location: "Jinja",
      duration: "2 days",
      price: "$300",
      rating: 4.7,
      image: "images/nile-expedition.jpg",
      description: "White-water rafting and adventure activities at the source of the Nile.",
    }
  ];

  function navigate(route) {
    dispatch('navigate', { route });
  }

  function book(type, item) {
    dispatch('book', { type, item });
  }
</script>

<div>
  <!-- Hero Section -->
  <section class="relative h-[80vh] min-h-[600px] bg-gray-900">
    <div class="absolute inset-0 bg-black opacity-40 z-10"></div>
    <div class="absolute inset-0 bg-[url('images/uganda-hero.jpg')] bg-cover bg-center"></div>
    
    <div class="relative z-20 container-custom h-full flex flex-col justify-center">
      <h1 class="text-4xl md:text-6xl font-bold text-white mb-4 leading-tight">
        Discover the <span class="text-accent">Pearl of Africa</span> with Shiloh Special
      </h1>
      <p class="text-xl md:text-2xl text-white max-w-2xl mb-8">
        Exceptional accommodations, seamless transportation, unforgettable tours, and personalized itineraries for your Ugandan adventure.
      </p>
      <div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4">
        <button 
          class="btn-primary text-lg py-3 px-8"
          on:click={() => navigate('itinerary')}
        >
          Plan Your Trip
        </button>
        <button 
          class="bg-white text-primary hover:bg-gray-100 transition-colors text-lg font-semibold py-3 px-8 rounded-md"
          on:click={() => navigate('tours')}
        >
          Explore Tours
        </button>
      </div>
    </div>
  </section>

  <!-- Services Section -->
  <section class="py-16 bg-gray-50">
    <div class="container-custom">
      <h2 class="text-3xl md:text-4xl font-bold text-center mb-4">Our Services</h2>
      <p class="text-center text-gray-600 max-w-2xl mx-auto mb-12">
        Shiloh Special offers comprehensive travel services to make your Ugandan experience exceptional from start to finish.
      </p>
      
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
        <!-- Accommodation -->
        <div class="card p-6 text-center hover:bg-gray-50 cursor-pointer" on:click={() => navigate('accommodations')}>
          <div class="bg-primary-light/10 p-4 rounded-full w-20 h-20 flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary" viewBox="0 0 20 20" fill="currentColor">
              <path d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-3">Premium Accommodations</h3>
          <p class="text-gray-600">
            From luxury hotels in Kampala to safari lodges in national parks, we offer the best accommodations across Uganda.
          </p>
        </div>
        
        <!-- Transportation -->
        <div class="card p-6 text-center hover:bg-gray-50 cursor-pointer" on:click={() => navigate('transport')}>
          <div class="bg-primary-light/10 p-4 rounded-full w-20 h-20 flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary" viewBox="0 0 20 20" fill="currentColor">
              <path d="M8 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM15 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z" />
              <path d="M3 4a1 1 0 00-1 1v10a1 1 0 001 1h1.05a2.5 2.5 0 014.9 0H11a1 1 0 001-1v-1h3.05a2.5 2.5 0 014.9 0H19a1 1 0 001-1v-6a1 1 0 00-.293-.707l-2-2A1 1 0 0017 4H3zM17 9V6.414L18.586 8H17v1zm-4 0V4h3v5h-3z" />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-3">Car & Transport Rental</h3>
          <p class="text-gray-600">
            Choose from our fleet of vehicles with professional drivers to take you safely around Uganda's stunning landscapes.
          </p>
        </div>
        
        <!-- Tours -->
        <div class="card p-6 text-center hover:bg-gray-50 cursor-pointer" on:click={() => navigate('tours')}>
          <div class="bg-primary-light/10 p-4 rounded-full w-20 h-20 flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary" viewBox="0 0 20 20" fill="currentColor">
              <path fill-rule="evenodd" d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z" clip-rule="evenodd" />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-3">Tours & Safaris</h3>
          <p class="text-gray-600">
            Guided tours to Uganda's national parks, cultural sites, and natural wonders with expert local guides.
          </p>
        </div>
        
        <!-- Itinerary Planning -->
        <div class="card p-6 text-center hover:bg-gray-50 cursor-pointer" on:click={() => navigate('itinerary')}>
          <div class="bg-primary-light/10 p-4 rounded-full w-20 h-20 flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-primary" viewBox="0 0 20 20" fill="currentColor">
              <path d="M9 2a1 1 0 000 2h2a1 1 0 100-2H9z" />
              <path fill-rule="evenodd" d="M4 5a2 2 0 012-2 3 3 0 003 3h2a3 3 0 003-3 2 2 0 012 2v11a2 2 0 01-2 2H6a2 2 0 01-2-2V5zm3 4a1 1 0 000 2h.01a1 1 0 100-2H7zm3 0a1 1 0 000 2h3a1 1 0 100-2h-3zm-3 4a1 1 0 100 2h.01a1 1 0 100-2H7zm3 0a1 1 0 100 2h3a1 1 0 100-2h-3z" clip-rule="evenodd" />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-3">Custom Itineraries</h3>
          <p class="text-gray-600">
            Personalized trip planning to create the perfect Ugandan adventure tailored to your preferences.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- Featured Accommodations -->
  <section class="py-16">
    <div class="container-custom">
      <div class="flex flex-col md:flex-row justify-between items-center mb-8">
        <div>
          <h2 class="text-3xl md:text-4xl font-bold mb-2">Featured Accommodations</h2>
          <p class="text-gray-600 max-w-2xl">
            Experience the best of Ugandan hospitality with our handpicked accommodations.
          </p>
        </div>
        <button 
          class="mt-4 md:mt-0 text-primary font-semibold flex items-center hover:text-primary-dark transition-colors"
          on:click={() => navigate('accommodations')}
        >
          View All
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M12.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
          </svg>
        </button>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        {#each featuredAccommodations as accommodation}
          <div class="card overflow-hidden">
            <div class="h-56 overflow-hidden">
              <img 
                src={accommodation.image} 
                alt={accommodation.name}
                class="w-full h-full object-cover transition-transform hover:scale-105"
              />
            </div>
            <div class="p-6">
              <div class="flex justify-between items-start mb-2">
                <h3 class="text-xl font-semibold">{accommodation.name}</h3>
                <span class="bg-primary-light/10 text-primary px-2 py-1 rounded-md text-sm font-medium">
                  {accommodation.price}/night
                </span>
              </div>
              <div class="flex items-center mb-3">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-accent" viewBox="0 0 20 20" fill="currentColor">
                  <path fill-rule="evenodd" d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z" clip-rule="evenodd" />
                </svg>
                <span class="ml-1 text-gray-600">{accommodation.location}</span>
              </div>
              <div class="flex items-center mb-3">
                <div class="flex">
                  {#each Array(5) as _, i}
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 {i < Math.floor(accommodation.rating) ? 'text-yellow-400' : 'text-gray-300'}" viewBox="0 0 20 20" fill="currentColor">
                      <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                    </svg>
                  {/each}
                </div>
                <span class="ml-1 text-gray-600">{accommodation.rating} ({Math.floor(Math.random() * 50) + 10} reviews)</span>
              </div>
              <p class="text-gray-600 mb-4">{accommodation.description}</p>
              <button 
                class="w-full btn-primary py-2"
                on:click={() => book('accommodation', accommodation)}
              >
                Book Now
              </button>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- Featured Tours -->
  <section class="py-16 bg-gray-50">
    <div class="container-custom">
      <div class="flex flex-col md:flex-row justify-between items-center mb-8">
        <div>
          <h2 class="text-3xl md:text-4xl font-bold mb-2">Featured Tours & Safaris</h2>
          <p class="text-gray-600 max-w-2xl">
            Experience Uganda's natural wonders and vibrant culture with our guided tours.
          </p>
        </div>
        <button 
          class="mt-4 md:mt-0 text-primary font-semibold flex items-center hover:text-primary-dark transition-colors"
          on:click={() => navigate('tours')}
        >
          View All
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-1" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M12.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
          </svg>
        </button>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        {#each featuredTours as tour}
          <div class="card overflow-hidden">
            <div class="h-56 overflow-hidden">
              <img 
                src={tour.image} 
                alt={tour.name}
                class="w-full h-full object-cover transition-transform hover:scale-105"
              />
            </div>
            <div class="p-6">
              <div class="flex justify-between items-start mb-2">
                <h3 class="text-xl font-semibold">{tour.name}</h3>
                <span class="bg-primary-light/10 text-primary px-2 py-1 rounded-md text-sm font-medium">
                  {tour.price}
                </span>
              </div>
              <div class="flex items-center justify-between mb-3">
                <div class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-accent" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z" clip-rule="evenodd" />
                  </svg>
                  <span class="ml-1 text-gray-600">{tour.location}</span>
                </div>
                <div class="flex items-center">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-accent" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-12a1 1 0 10-2 0v4a1 1 0 00.293.707l2.828 2.829a1 1 0 101.415-1.415L11 9.586V6z" clip-rule="evenodd" />
                  </svg>
                  <span class="ml-1 text-gray-600">{tour.duration}</span>
                </div>
              </div>
              <div class="flex items-center mb-3">
                <div class="flex">
                  {#each Array(5) as _, i}
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 {i < Math.floor(tour.rating) ? 'text-yellow-400' : 'text-gray-300'}" viewBox="0 0 20 20" fill="currentColor">
                      <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                    </svg>
                  {/each}
                </div>
                <span class="ml-1 text-gray-600">{tour.rating} ({Math.floor(Math.random() * 50) + 10} reviews)</span>
              </div>
              <p class="text-gray-600 mb-4">{tour.description}</p>
              <button 
                class="w-full btn-primary py-2"
                on:click={() => book('tour', tour)}
              >
                Book Now
              </button>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- Testimonials -->
  <section class="py-16 bg-primary text-white">
    <div class="container-custom">
      <h2 class="text-3xl md:text-4xl font-bold text-center mb-2">What Our Clients Say</h2>
      <p class="text-center text-primary-light max-w-2xl mx-auto mb-12">
        Discover why travelers choose Shiloh Special for their Ugandan adventures.
      </p>
      
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <!-- Testimonial 1 -->
        <div class="bg-white/10 backdrop-blur-sm p-6 rounded-lg">
          <div class="flex mb-4">
            {#each Array(5) as _}
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
              </svg>
            {/each}
          </div>
          <p class="mb-4 italic">
            "Our safari tour with Shiloh Special was the highlight of our trip to Africa. The guides were knowledgeable, accommodations were fantastic, and we saw all the Big Five! Can't recommend them enough."
          </p>
          <div class="flex items-center">
            <div class="rounded-full bg-gray-200 h-12 w-12 flex items-center justify-center text-primary font-bold mr-3">
              JD
            </div>
            <div>
              <h4 class="font-semibold">John Davis</h4>
              <p class="text-sm text-primary-light">New York, USA</p>
            </div>
          </div>
        </div>
        
        <!-- Testimonial 2 -->
        <div class="bg-white/10 backdrop-blur-sm p-6 rounded-lg">
          <div class="flex mb-4">
            {#each Array(5) as _}
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
              </svg>
            {/each}
          </div>
          <p class="mb-4 italic">
            "The custom itinerary Shiloh put together for our family was perfect. They balanced wildlife experiences with cultural activities that kept our teenagers engaged throughout the trip. Our driver was exceptional!"
          </p>
          <div class="flex items-center">
            <div class="rounded-full bg-gray-200 h-12 w-12 flex items-center justify-center text-primary font-bold mr-3">
              SM
            </div>
            <div>
              <h4 class="font-semibold">Sarah Miller</h4>
              <p class="text-sm text-primary-light">London, UK</p>
            </div>
          </div>
        </div>
        
        <!-- Testimonial 3 -->
        <div class="bg-white/10 backdrop-blur-sm p-6 rounded-lg">
          <div class="flex mb-4">
            {#each Array(5) as _}
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
              </svg>
            {/each}
          </div>
          <p class="mb-4 italic">
            "Gorilla trekking in Bwindi was a dream come true. Shiloh handled all the permits, logistics, and accommodations perfectly. The experience of seeing gorillas in their natural habitat was life-changing."
          </p>
          <div class="flex items-center">
            <div class="rounded-full bg-gray-200 h-12 w-12 flex items-center justify-center text-primary font-bold mr-3">
              AK
            </div>
            <div>
              <h4 class="font-semibold">Akiko Tanaka</h4>
              <p class="text-sm text-primary-light">Tokyo, Japan</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- CTA -->
  <section class="py-16">
    <div class="container-custom">
      <div class="bg-accent rounded-lg p-8 md:p-12 flex flex-col md:flex-row items-center justify-between">
        <div class="mb-6 md:mb-0 md:mr-8">
          <h2 class="text-3xl md:text-4xl font-bold text-white mb-4">Ready to Explore Uganda?</h2>
          <p class="text-white/90 text-lg mb-0 max-w-xl">
            Let us help you plan your perfect Ugandan adventure. From accommodations to tours, we'll handle everything so you can focus on making memories.
          </p>
        </div>
        <button 
          class="bg-white text-accent hover:bg-gray-100 transition-colors text-lg font-semibold py-3 px-8 rounded-md shadow-lg flex-shrink-0"
          on:click={() => navigate('contact')}
        >
          Contact Us Now
        </button>
      </div>
    </div>
  </section>
</div>