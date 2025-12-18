# silver-journey
ELEMENTS OF THE UNIVERSE IS A SPACE EXPLORATION ENTHUSIAST WEBSITE 
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elements of the Universe | Exploration & Research</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;700&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --neon-blue: #00f3ff;
            --deep-space: #050510;
            --starlight: #ffffff;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--deep-space);
            color: var(--starlight);
            overflow-x: hidden;
        }

        h1, h2, h3, h4, h5, .font-display {
            font-family: 'Space Grotesk', sans-serif;
        }

        /* Starfield Canvas behind everything */
        #starfield {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.8;
        }

        /* Glassmorphism Utilities */
        .glass-panel {
            background: rgba(20, 20, 35, 0.4);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }

        .glass-nav {
            background: rgba(5, 5, 16, 0.85);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Animations */
        @keyframes pulse-glow {
            0%, 100% { box-shadow: 0 0 10px rgba(0, 243, 255, 0.2); }
            50% { box-shadow: 0 0 20px rgba(0, 243, 255, 0.5); }
        }

        .animate-glow {
            animation: pulse-glow 3s infinite;
        }

        .hover-lift {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .hover-lift:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px -10px rgba(0, 243, 255, 0.3);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #050510;
        }
        ::-webkit-scrollbar-thumb {
            background: #333;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #00f3ff;
        }

        /* Planet Orbit Animation helper */
        .orbit-container {
            position: relative;
            width: 300px;
            height: 300px;
        }
        .planet {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            border-radius: 50%;
        }
    </style>
</head>
<body class="antialiased selection:bg-cyan-500 selection:text-black">

    <!-- Background Canvas -->
    <canvas id="starfield"></canvas>

    <!-- Navigation -->
    <nav class="fixed w-full z-50 glass-nav transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <div class="flex-shrink-0 flex items-center gap-2 cursor-pointer" onclick="window.scrollTo(0,0)">
                    <i data-lucide="orbit" class="h-8 w-8 text-cyan-400"></i>
                    <span class="font-display font-bold text-xl tracking-wider text-white">EOU <span class="text-cyan-400">AGENCY</span></span>
                </div>
                
                <!-- Desktop Menu -->
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-8">
                        <a href="#missions" class="hover:text-cyan-400 px-3 py-2 rounded-md text-sm font-medium transition-colors">Missions</a>
                        <a href="#technology" class="hover:text-cyan-400 px-3 py-2 rounded-md text-sm font-medium transition-colors">Technology</a>
                        <a href="#research" class="hover:text-cyan-400 px-3 py-2 rounded-md text-sm font-medium transition-colors">Research</a>
                        <a href="#news" class="hover:text-cyan-400 px-3 py-2 rounded-md text-sm font-medium transition-colors">News</a>
                        <button class="bg-cyan-500 hover:bg-cyan-400 text-black px-4 py-2 rounded-full font-bold text-sm transition-all transform hover:scale-105">
                            Live Data
                        </button>
                    </div>
                </div>

                <!-- Mobile menu button -->
                <div class="-mr-2 flex md:hidden">
                    <button type="button" onclick="toggleMobileMenu()" class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-800 focus:outline-none">
                        <i data-lucide="menu" class="h-6 w-6"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu Panel -->
        <div class="md:hidden hidden glass-panel border-t border-gray-800" id="mobile-menu">
            <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
                <a href="#missions" class="text-gray-300 hover:text-white block px-3 py-2 rounded-md text-base font-medium">Missions</a>
                <a href="#technology" class="text-gray-300 hover:text-white block px-3 py-2 rounded-md text-base font-medium">Technology</a>
                <a href="#research" class="text-gray-300 hover:text-white block px-3 py-2 rounded-md text-base font-medium">Research</a>
                <a href="#news" class="text-gray-300 hover:text-white block px-3 py-2 rounded-md text-base font-medium">News</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="relative pt-32 pb-20 lg:pt-48 lg:pb-32 overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 text-center">
            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-cyan-500/30 bg-cyan-500/10 text-cyan-400 text-xs font-semibold tracking-wide uppercase mb-8 animate-glow">
                <span class="w-2 h-2 rounded-full bg-cyan-400 animate-pulse"></span>
                System Operational
            </div>
            <h1 class="text-5xl md:text-7xl lg:text-8xl font-display font-bold text-white mb-6 tracking-tight leading-none">
                DECODING THE <br />
                <span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-purple-500">UNIVERSE</span>
            </h1>
            <p class="mt-4 max-w-2xl mx-auto text-xl text-gray-400 font-light">
                Exploring the unknown frontiers of deep space. From the icy moons of Jupiter to the exoplanets of Andromeda, we go where humanity has never dreamed.
            </p>
            <div class="mt-10 flex justify-center gap-4">
                <a href="#missions" class="px-8 py-4 border border-cyan-500 bg-cyan-500/10 hover:bg-cyan-500 hover:text-black text-cyan-400 font-bold rounded-none uppercase tracking-widest transition-all duration-300">
                    Explore Missions
                </a>
                <a href="#research" class="px-8 py-4 border border-white/20 hover:border-white text-white font-bold rounded-none uppercase tracking-widest transition-all duration-300">
                    View Research
                </a>
            </div>
        </div>
        
        <!-- Decorative abstract planet -->
        <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-purple-900/10 rounded-full blur-3xl -z-10"></div>
    </header>

    <!-- Live Telemetry / Stats -->
    <section class="border-y border-white/10 bg-black/30 backdrop-blur-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-8 py-12">
                <div class="text-center">
                    <p class="text-gray-500 text-xs font-mono uppercase tracking-widest mb-2">Active Probes</p>
                    <p class="text-4xl font-display font-bold text-white" id="stat-probes">0</p>
                </div>
                <div class="text-center">
                    <p class="text-gray-500 text-xs font-mono uppercase tracking-widest mb-2">Distance Covered (AU)</p>
                    <p class="text-4xl font-display font-bold text-cyan-400" id="stat-distance">0.00</p>
                </div>
                <div class="text-center">
                    <p class="text-gray-500 text-xs font-mono uppercase tracking-widest mb-2">Data Downlinked (PB)</p>
                    <p class="text-4xl font-display font-bold text-white" id="stat-data">0</p>
                </div>
                <div class="text-center">
                    <p class="text-gray-500 text-xs font-mono uppercase tracking-widest mb-2">Current Speed (km/s)</p>
                    <p class="text-4xl font-display font-bold text-purple-400" id="stat-speed">17.4</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Active Missions -->
    <section id="missions" class="py-24 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex flex-col md:flex-row justify-between items-end mb-16">
                <div>
                    <h2 class="text-4xl font-display font-bold text-white mb-4">Active Missions</h2>
                    <p class="text-gray-400 max-w-lg">Current directives pushing the boundaries of our solar system and acquiring vital data for the future of humanity.</p>
                </div>
                <a href="#" class="hidden md:flex items-center text-cyan-400 hover:text-cyan-300 transition-colors mt-4 md:mt-0 group">
                    View Full Flight Log <i data-lucide="arrow-right" class="ml-2 w-4 h-4 transform group-hover:translate-x-1 transition-transform"></i>
                </a>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Mission Card 1 -->
                <div class="glass-panel rounded-xl overflow-hidden hover-lift group cursor-pointer">
                    <div class="h-48 overflow-hidden relative">
                        <img src="https://images.unsplash.com/photo-1614728853913-1e22ba074413?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Mars Mission" class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-700">
                        <div class="absolute top-4 left-4 bg-red-600 text-white text-xs font-bold px-2 py-1 rounded uppercase">Mars</div>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-white font-display">Ares Redux</h3>
                            <i data-lucide="activity" class="text-green-400 w-5 h-5"></i>
                        </div>
                        <p class="text-gray-400 text-sm mb-4">Establishing the first permanent atmospheric monitoring station on the chaotic terrain of Mars.</p>
                        <div class="flex items-center justify-between pt-4 border-t border-white/10">
                            <span class="text-xs font-mono text-gray-500">T+ 422 DAYS</span>
                            <span class="text-xs font-mono text-cyan-400">NOMINAL</span>
                        </div>
                    </div>
                </div>

                <!-- Mission Card 2 -->
                <div class="glass-panel rounded-xl overflow-hidden hover-lift group cursor-pointer">
                    <div class="h-48 overflow-hidden relative">
                        <img src="https://images.unsplash.com/photo-1614726365723-49cfae5004ca?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Europa Mission" class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-700">
                        <div class="absolute top-4 left-4 bg-cyan-600 text-white text-xs font-bold px-2 py-1 rounded uppercase">Europa</div>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-white font-display">Deep Core</h3>
                            <i data-lucide="wifi" class="text-yellow-400 w-5 h-5 animate-pulse"></i>
                        </div>
                        <p class="text-gray-400 text-sm mb-4">Drilling beneath the ice sheets of Jupiter's moon to search for microbial life in the subsurface ocean.</p>
                        <div class="flex items-center justify-between pt-4 border-t border-white/10">
                            <span class="text-xs font-mono text-gray-500">T- 45 DAYS TO ARRIVAL</span>
                            <span class="text-xs font-mono text-cyan-400">TRANSIT</span>
                        </div>
                    </div>
                </div>

                <!-- Mission Card 3 -->
                <div class="glass-panel rounded-xl overflow-hidden hover-lift group cursor-pointer">
                    <div class="h-48 overflow-hidden relative">
                        <img src="https://images.unsplash.com/photo-1462331940025-496dfbfc7564?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Nebula Watch" class="w-full h-full object-cover transform group-hover:scale-110 transition-transform duration-700">
                        <div class="absolute top-4 left-4 bg-purple-600 text-white text-xs font-bold px-2 py-1 rounded uppercase">Deep Space</div>
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-white font-display">Void Gazer</h3>
                            <i data-lucide="radio" class="text-purple-400 w-5 h-5"></i>
                        </div>
                        <p class="text-gray-400 text-sm mb-4">Mapping the cosmic microwave background radiation to understand the earliest moments of the universe.</p>
                        <div class="flex items-center justify-between pt-4 border-t border-white/10">
                            <span class="text-xs font-mono text-gray-500">OPERATIONAL SINCE 2028</span>
                            <span class="text-xs font-mono text-cyan-400">GATHERING</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Mission Control / Technology -->
    <section id="technology" class="py-24 bg-gradient-to-b from-transparent to-black/50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
                <div>
                    <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-purple-500/10 text-purple-400 text-xs font-semibold tracking-wide uppercase mb-6">
                        Next Gen Tech
                    </div>
                    <h2 class="text-4xl md:text-5xl font-display font-bold text-white mb-6">The Titan Propulsion System</h2>
                    <p class="text-gray-300 text-lg mb-8 leading-relaxed">
                        Conventional chemical rockets can only take us so far. The new Titan Ion Drive creates a continuous thrust capable of reaching 15% light speed, putting Alpha Centauri within reach of a human lifetime.
                    </p>
                    
                    <ul class="space-y-4 mb-8">
                        <li class="flex items-start">
                            <div class="flex-shrink-0 w-6 h-6 rounded-full bg-cyan-500/20 flex items-center justify-center mt-1">
                                <i data-lucide="check" class="w-3 h-3 text-cyan-400"></i>
                            </div>
                            <span class="ml-4 text-gray-300">Zero-Point Energy Harvesting modules</span>
                        </li>
                        <li class="flex items-start">
                            <div class="flex-shrink-0 w-6 h-6 rounded-full bg-cyan-500/20 flex items-center justify-center mt-1">
                                <i data-lucide="check" class="w-3 h-3 text-cyan-400"></i>
                            </div>
                            <span class="ml-4 text-gray-300">Self-healing Graphene Hull structure</span>
                        </li>
                        <li class="flex items-start">
                            <div class="flex-shrink-0 w-6 h-6 rounded-full bg-cyan-500/20 flex items-center justify-center mt-1">
                                <i data-lucide="check" class="w-3 h-3 text-cyan-400"></i>
                            </div>
                            <span class="ml-4 text-gray-300">AI-driven navigation autonomy</span>
                        </li>
                    </ul>

                    <button class="text-white border-b border-cyan-500 pb-1 hover:text-cyan-400 transition-colors">
                        Read Technical Paper &rarr;
                    </button>
                </div>
                
                <div class="relative">
                    <!-- Decorative tech circle -->
                    <div class="relative aspect-square w-full max-w-md mx-auto">
                        <div class="absolute inset-0 rounded-full border border-dashed border-cyan-500/30 animate-[spin_10s_linear_infinite]"></div>
                        <div class="absolute inset-4 rounded-full border border-white/10 animate-[spin_15s_linear_infinite_reverse]"></div>
                        <div class="absolute inset-0 flex items-center justify-center">
                            <div class="w-32 h-32 rounded-full bg-cyan-500 blur-3xl opacity-20 animate-pulse"></div>
                            <img src="https://images.unsplash.com/photo-1581093458791-9f3c3900df4b?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Engine" class="w-64 h-64 object-cover rounded-full border-4 border-black relative z-10 grayscale hover:grayscale-0 transition-all duration-500">
                        </div>
                        
                        <!-- Floating Cards -->
                        <div class="absolute top-0 right-0 glass-panel p-4 rounded-lg transform translate-x-4 -translate-y-4 animate-bounce" style="animation-duration: 3s">
                            <p class="text-xs text-gray-400 uppercase">Thrust Capacity</p>
                            <p class="text-xl font-bold text-cyan-400">450 MN</p>
                        </div>
                        <div class="absolute bottom-10 left-0 glass-panel p-4 rounded-lg transform -translate-x-4 translate-y-4 animate-bounce" style="animation-duration: 4s">
                            <p class="text-xs text-gray-400 uppercase">Efficiency</p>
                            <p class="text-xl font-bold text-green-400">99.98%</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Latest News Grid -->
    <section id="news" class="py-24">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-4xl font-display font-bold text-white mb-12 text-center">Transmission Log</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <!-- News 1 -->
                <div class="col-span-1 lg:col-span-2 glass-panel rounded-xl overflow-hidden relative group h-64 md:h-auto">
                    <img src="https://images.unsplash.com/photo-1451187580459-43490279c0fa?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-105 opacity-60 group-hover:opacity-40">
                    <div class="absolute bottom-0 left-0 p-8 w-full bg-gradient-to-t from-black to-transparent">
                        <span class="text-cyan-400 text-xs font-bold uppercase tracking-wider mb-2 block">Discovery</span>
                        <h3 class="text-2xl font-bold text-white mb-2">Water Vapor detected on K2-18b</h3>
                        <p class="text-gray-300 text-sm line-clamp-2">Spectroscopic analysis reveals potential habitable conditions on the distant super-earth.</p>
                    </div>
                </div>

                <!-- News 2 -->
                <div class="glass-panel p-6 rounded-xl border-l-4 border-cyan-500 hover:bg-white/5 transition-colors">
                    <span class="text-gray-500 text-xs mb-2 block">Dec 14, 2025</span>
                    <h4 class="text-lg font-bold text-white mb-3">Launch Window Confirmed</h4>
                    <p class="text-gray-400 text-sm">The Artemis VI payload has been secured and weather conditions are optimal for the Tuesday launch.</p>
                    <a href="#" class="text-cyan-400 text-sm mt-4 inline-block hover:underline">Read briefing</a>
                </div>

                <!-- News 3 -->
                <div class="glass-panel p-6 rounded-xl border-l-4 border-purple-500 hover:bg-white/5 transition-colors">
                    <span class="text-gray-500 text-xs mb-2 block">Dec 12, 2025</span>
                    <h4 class="text-lg font-bold text-white mb-3">Signal Received</h4>
                    <p class="text-gray-400 text-sm">Voyager 3 has sent back the first ever high-res images of the Oort Cloud objects.</p>
                    <a href="#" class="text-purple-400 text-sm mt-4 inline-block hover:underline">View Gallery</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Join Section -->
    <section class="py-24">
        <div class="max-w-4xl mx-auto px-4 text-center">
            <h2 class="text-3xl md:text-5xl font-display font-bold text-white mb-6">Join the Elements</h2>
            <p class="text-gray-300 text-lg mb-8">We are looking for engineers, astrophysicists, and dreamers. Help us decode the universe.</p>
            <div class="glass-panel p-2 rounded-full inline-flex max-w-md w-full">
                <input type="email" placeholder="Enter your frequency (email)..." class="bg-transparent border-none text-white px-6 py-3 w-full focus:outline-none focus:ring-0">
                <button class="bg-white text-black font-bold px-8 py-3 rounded-full hover:bg-cyan-400 transition-colors whitespace-nowrap">
                    Subscribe
                </button>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="border-t border-white/10 bg-black py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
                <div class="col-span-1 md:col-span-2">
                    <div class="flex items-center gap-2 mb-4">
                        <i data-lucide="orbit" class="h-6 w-6 text-cyan-400"></i>
                        <span class="font-display font-bold text-xl tracking-wider text-white">EOU</span>
                    </div>
                    <p class="text-gray-500 text-sm max-w-xs">
                        Elements of the Universe is a private research organization dedicated to the exploration and understanding of deep space phenomena.
                    </p>
                </div>
                <div>
                    <h4 class="text-white font-bold mb-4">Sectors</h4>
                    <ul class="space-y-2 text-gray-500 text-sm">
                        <li><a href="#" class="hover:text-cyan-400">Exoplanet Research</a></li>
                        <li><a href="#" class="hover:text-cyan-400">Propulsion Labs</a></li>
                        <li><a href="#" class="hover:text-cyan-400">Astrobiology</a></li>
                        <li><a href="#" class="hover:text-cyan-400">Human Spaceflight</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-white font-bold mb-4">Connect</h4>
                    <div class="flex space-x-4">
                        <a href="#" class="text-gray-500 hover:text-white"><i data-lucide="twitter" class="w-5 h-5"></i></a>
                        <a href="#" class="text-gray-500 hover:text-white"><i data-lucide="instagram" class="w-5 h-5"></i></a>
                        <a href="#" class="text-gray-500 hover:text-white"><i data-lucide="youtube" class="w-5 h-5"></i></a>
                    </div>
                </div>
            </div>
            <div class="border-t border-white/10 pt-8 flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-600 text-xs">&copy; 2025 Elements of the Universe. All systems nominal.</p>
                <div class="flex space-x-6 mt-4 md:mt-0">
                    <a href="#" class="text-gray-600 text-xs hover:text-white">Privacy</a>
                    <a href="#" class="text-gray-600 text-xs hover:text-white">Terms</a>
                    <a href="#" class="text-gray-600 text-xs hover:text-white">Security</a>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Initialize Lucide Icons
        lucide.createIcons();

        // Navbar Scroll Effect
        window.addEventListener('scroll', () => {
            const nav = document.getElementById('navbar');
            if (window.scrollY > 50) {
                nav.classList.add('shadow-lg');
                nav.style.background = 'rgba(5, 5, 16, 0.95)';
            } else {
                nav.classList.remove('shadow-lg');
                nav.style.background = 'rgba(5, 5, 16, 0.85)';
            }
        });

        // Mobile Menu Toggle
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        // --- Starfield Canvas Animation ---
        const canvas = document.getElementById('starfield');
        const ctx = canvas.getContext('2d');
        let width, height;
        let stars = [];

        function initCanvas() {
            width = window.innerWidth;
            height = window.innerHeight;
            canvas.width = width;
            canvas.height = height;
            createStars();
        }

        function createStars() {
            stars = [];
            const count = Math.floor(width * height / 3000); // Responsive star count
            for (let i = 0; i < count; i++) {
                stars.push({
                    x: Math.random() * width,
                    y: Math.random() * height,
                    z: Math.random() * 2, // Depth
                    size: Math.random() * 1.5,
                    brightness: Math.random(),
                    speed: Math.random() * 0.05 + 0.01
                });
            }
        }

        function animateStars() {
            ctx.clearRect(0, 0, width, height);
            
            // Draw background gradient
            const gradient = ctx.createLinearGradient(0, 0, 0, height);
            gradient.addColorStop(0, '#050510');
            gradient.addColorStop(1, '#0a0a20');
            ctx.fillStyle = gradient;
            ctx.fillRect(0, 0, width, height);

            ctx.fillStyle = '#ffffff';
            
            stars.forEach(star => {
                // Move star
                star.y -= star.speed * (star.z + 0.5); // Parallax effect
                
                // Reset if off screen
                if (star.y < 0) {
                    star.y = height;
                    star.x = Math.random() * width;
                }

                // Draw star
                ctx.globalAlpha = star.brightness * (Math.sin(Date.now() * 0.001 * star.speed * 100) + 1.2) / 2; // Twinkle
                ctx.beginPath();
                ctx.arc(star.x, star.y, star.size * star.z, 0, Math.PI * 2);
                ctx.fill();
            });
            ctx.globalAlpha = 1;
            requestAnimationFrame(animateStars);
        }

        window.addEventListener('resize', initCanvas);
        initCanvas();
        animateStars();

        // --- Number Counting Animation ---
        function animateValue(obj, start, end, duration, isFloat = false) {
            let startTimestamp = null;
            const step = (timestamp) => {
                if (!startTimestamp) startTimestamp = timestamp;
                const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                const value = progress * (end - start) + start;
                obj.innerHTML = isFloat ? value.toFixed(2) : Math.floor(value);
                if (progress < 1) {
                    window.requestAnimationFrame(step);
                }
            };
            window.requestAnimationFrame(step);
        }

        // Trigger animations when stats come into view
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateValue(document.getElementById('stat-probes'), 0, 12, 2000);
                    animateValue(document.getElementById('stat-distance'), 0, 42.8, 2500, true);
                    animateValue(document.getElementById('stat-data'), 0, 850, 2000);
                    // Speed updates slightly to look live
                    setInterval(() => {
                        const base = 17.4;
                        const variation = (Math.random() - 0.5) * 0.1;
                        document.getElementById('stat-speed').innerText = (base + variation).toFixed(2);
                    }, 500);
                    observer.disconnect();
                }
            });
        }, { threshold: 0.5 });

        observer.observe(document.getElementById('stat-probes'));

    </script>
</body>
</html>
