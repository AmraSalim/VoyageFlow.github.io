<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>VoyageFlow — Interactive Travel Experience Simulator</title>
  <!-- Tailwind via CDN (optional utility) -->
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    html { scroll-behavior: smooth; }
    /* Simple modal animations */
    .modal-backdrop { background: rgba(0,0,0,0.5); }
    .hidden-pane { display: none; }
    /* Page container sizing */
    .page { min-height: 100vh; padding: 2rem; }
    /* For sticky nav on blog page */
    .sticky-top { position: sticky; top: 0; z-index: 40; }
    /* Small tweaks */
    .chip { background: rgba(255,255,255,0.06); border-radius: 9999px; padding: 0.25rem 0.75rem; }
  </style>
</head>
<body class="bg-gradient-to-b from-sky-50 to-white text-slate-800">
  <!-- App wrapper: simulate pages by toggling display -->
  <div id="app" class="max-w-5xl mx-auto">

    <!-- PAGE 1: Registration -->
    <section id="page-register" class="page bg-white rounded-2xl shadow-lg my-8 p-8">
      <h1 class="text-3xl font-extrabold mb-2">VoyageFlow</h1>
      <p class="text-slate-600 mb-6">Create your account to start a simulated journey — no backend required.</p>

      <form id="regForm" class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div>
          <label class="block text-sm font-medium">Full Name</label>
          <input id="fullName" required class="mt-1 block w-full rounded-md border-gray-200 shadow-sm px-3 py-2" placeholder="Asha Patel" />
        </div>
        <div>
          <label class="block text-sm font-medium">Email</label>
          <input id="email" required type="email" class="mt-1 block w-full rounded-md border-gray-200 shadow-sm px-3 py-2" placeholder="you@domain.com" />
          <p id="emailError" class="text-red-600 text-sm mt-1 hidden">Enter a valid email address.</p>
        </div>

        <div>
          <label class="block text-sm font-medium">Phone Number</label>
          <input id="phone" required maxlength="10" inputmode="numeric" class="mt-1 block w-full rounded-md border-gray-200 shadow-sm px-3 py-2" placeholder="10 digits" />
          <p id="phoneError" class="text-red-600 text-sm mt-1 hidden">Phone must be exactly 10 digits.</p>
        </div>

        <div>
          <label class="block text-sm font-medium">PIN Code</label>
          <input id="pincode" required maxlength="6" inputmode="numeric" class="mt-1 block w-full rounded-md border-gray-200 shadow-sm px-3 py-2" placeholder="6 digits" />
          <p id="pinError" class="text-red-600 text-sm mt-1 hidden">PIN code must be exactly 6 digits.</p>
        </div>

        <div class="md:col-span-2">
          <label class="block text-sm font-medium">Short Bio</label>
          <textarea id="bio" rows="3" class="mt-1 block w-full rounded-md border-gray-200 shadow-sm px-3 py-2" placeholder="Tell us about yourself (optional)"></textarea>
        </div>

        <div class="md:col-span-2 flex items-center justify-between">
          <div class="text-sm text-slate-600">By continuing you agree to this demo's <span class="underline">terms</span>.</div>
          <div>
            <button type="button" id="regSubmit" class="bg-sky-600 text-white px-4 py-2 rounded-md shadow hover:bg-sky-700">Submit</button>
          </div>
        </div>
      </form>

      <p class="text-xs text-slate-500 mt-4">Tip: Try invalid inputs to see validation messages, then correct them.</p>
    </section>

    <!-- PAGE 2: Travel Blog -->
    <section id="page-blog" class="page bg-white rounded-2xl shadow-lg my-8 p-0 hidden-pane">
      <div class="sticky-top bg-white/80 backdrop-blur-md border-b px-6 py-4">
        <div class="max-w-5xl mx-auto flex items-center justify-between">
          <div class="flex items-center gap-4">
            <h2 class="text-xl font-bold">VoyageFlow — Destinations</h2>
            <span class="chip">Explore</span>
          </div>
          <nav class="flex gap-3" aria-label="Section navigation">
            <a class="px-3 py-2 hover:underline" href="#paris">Paris</a>
            <a class="px-3 py-2 hover:underline" href="#tokyo">Tokyo</a>
            <a class="px-3 py-2 hover:underline" href="#rome">Rome</a>
            <a class="px-3 py-2 hover:underline" href="#cape">Cape Town</a>
            <a class="px-3 py-2 hover:underline" href="#lax">Los Angeles</a>
          </nav>
        </div>
      </div>

      <div class="p-8 space-y-12">
        <!-- 5 content sections -->
        <article id="paris" class="prose max-w-none">
          <h3 class="text-2xl font-semibold">Paris — City of Lights</h3>
          <p>Stroll along the Seine, sip coffee in Montmartre and admire the Eiffel Tower's twinkling lights. Ideal for romance, art lovers and anyone who appreciates croissants.</p>
        </article>

        <article id="tokyo" class="prose max-w-none">
          <h3 class="text-2xl font-semibold">Tokyo — Neon Metropolis</h3>
          <p>From Shibuya crossings to tranquil temples, Tokyo blends futurism with tradition. Foodies will adore the ramen alleyways and izakaya culture.</p>
        </article>

        <article id="rome" class="prose max-w-none">
          <h3 class="text-2xl font-semibold">Rome — Ancient Wonders</h3>
          <p>Walk the Colosseum, toss a coin into Trevi Fountain, and savor world-class gelato in narrow cobbled streets.</p>
        </article>

        <article id="cape" class="prose max-w-none">
          <h3 class="text-2xl font-semibold">Cape Town — Coastal Charm</h3>
          <p>From Table Mountain views to rugged coastlines, Cape Town is a dream for outdoor lovers and wine enthusiasts alike.</p>
        </article>

        <article id="lax" class="prose max-w-none">
          <h3 class="text-2xl font-semibold">Los Angeles — Golden Dreams</h3>
          <img src="https://rare-gallery.com/thumbs/864481-Golden-Gate-Bridge-USA-Bridges-Los-Angeles-California.jpg"
          alt="Los Angeles - Hollywood Sign"
          class="w-full h-64 object-cover rounded-xl mb-4 shadow">
          <p>Sun, beaches and iconic entertainment — LA offers a taste of Hollywood glamour along with diverse neighborhoods and cuisine.</p>
        </article>

        <div class="text-center mt-6">
          <button id="toPlanner" class="bg-emerald-600 text-white px-5 py-3 rounded-md shadow hover:bg-emerald-700">Plan Your Trip →</button>
        </div>
      </div>
    </section>

    <!-- PAGE 3: Itinerary & Price Calculator -->
    <section id="page-planner" class="page bg-white rounded-2xl shadow-lg my-8 p-8 hidden-pane">
      <h2 class="text-2xl font-bold mb-4">Build Your Trip</h2>
      <p class="text-slate-600 mb-6">Select travel options, food packages and activities. Total updates live as you choose.</p>

      <form id="plannerForm" class="space-y-6">
        <div class="grid md:grid-cols-3 gap-4">
          <fieldset class="p-4 border rounded-md">
            <legend class="font-semibold">Travel Options</legend>
            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="300" data-name="Economy Flight" />
                <span class="ml-2">Economy Flight</span>
              </div>
              <div class="font-medium">$300</div>
            </label>

            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="800" data-name="Business Flight" />
                <span class="ml-2">Business Flight</span>
              </div>
              <div class="font-medium">$800</div>
            </label>

            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="150" data-name="Train + Bus" />
                <span class="ml-2">Train + Bus</span>
              </div>
              <div class="font-medium">$150</div>
            </label>
          </fieldset>

          <fieldset class="p-4 border rounded-md">
            <legend class="font-semibold">Food Packages</legend>
            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="50" data-name="Local Food Tour" />
                <span class="ml-2">Local Food Tour</span>
              </div>
              <div class="font-medium">$50</div>
            </label>

            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="80" data-name="Gourmet Experience" />
                <span class="ml-2">Gourmet Experience</span>
              </div>
              <div class="font-medium">$80</div>
            </label>

            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="25" data-name="Breakfast Add-on" />
                <span class="ml-2">Breakfast Add-on</span>
              </div>
              <div class="font-medium">$25</div>
            </label>
          </fieldset>

          <fieldset class="p-4 border rounded-md">
            <legend class="font-semibold">Activities</legend>
            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="120" data-name="City Tour" />
                <span class="ml-2">City Tour</span>
              </div>
              <div class="font-medium">$120</div>
            </label>

            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="200" data-name="Adventure Day" />
                <span class="ml-2">Adventure Day</span>
              </div>
              <div class="font-medium">$200</div>
            </label>

            <label class="flex items-center justify-between mt-3">
              <div>
                <input type="checkbox" class="optionCheckbox" data-price="40" data-name="Museum Pass" />
                <span class="ml-2">Museum Pass</span>
              </div>
              <div class="font-medium">$40</div>
            </label>
          </fieldset>
        </div>

        <div class="flex items-center justify-between mt-6">
          <div class="text-lg">Selected: <span id="selectedList" class="font-medium">None</span></div>
          <div class="text-2xl font-extrabold">Total: $<span id="totalPrice">0</span></div>
        </div>

        <div class="flex gap-3">
          <button id="confirmPlan" type="button" class="bg-rose-600 text-white px-5 py-3 rounded-md shadow hover:bg-rose-700">Confirm & Continue</button>
          <button id="backToBlog" type="button" class="px-5 py-3 rounded-md border hover:bg-slate-50">Back to Blog</button>
        </div>
      </form>
    </section>

    <!-- PAGE 4: Confirmation / Thank You -->
    <section id="page-confirm" class="page bg-white rounded-2xl shadow-lg my-8 p-8 hidden-pane text-center">
      <h2 class="text-3xl font-bold">Thank You!</h2>
      <p class="text-slate-600 mt-2">Your booking has been simulated successfully.</p>

      <div class="mt-6 prose mx-auto max-w-none">
        <h3>Summary</h3>
        <p id="summaryText">No selections found.</p>
      </div>

      <div class="mt-8 flex justify-center gap-4">
        <button id="startOver" class="px-5 py-3 rounded-md bg-sky-600 text-white hover:bg-sky-700">Start Over</button>
        <a href="#" class="px-5 py-3 rounded-md border">Share (demo)</a>
      </div>
    </section>

  </div>

  <!-- Modals: Registration Success & Confirmation -->
  <div id="modal" class="fixed inset-0 hidden flex items-center justify-center modal-backdrop">
    <div class="bg-white rounded-lg shadow-xl max-w-md w-full p-6">
      <h3 id="modalTitle" class="text-xl font-bold">Success</h3>
      <p id="modalMessage" class="mt-3 text-slate-600">You're registered.</p>
      <div class="mt-6 text-right">
        <button id="modalClose" class="px-4 py-2 bg-slate-200 rounded-md">Close</button>
      </div>
    </div>
  </div>

  <script>
    // Simple page manager
    const pages = {
      register: document.getElementById('page-register'),
      blog: document.getElementById('page-blog'),
      planner: document.getElementById('page-planner'),
      confirm: document.getElementById('page-confirm')
    };

    function showPage(name) {
      Object.values(pages).forEach(p => p.classList.add('hidden-pane'));
      pages[name].classList.remove('hidden-pane');
      // scroll top for visible page
      pages[name].scrollTop = 0;
      window.scrollTo({ top: 0 });
    }

    // Start at registration
    showPage('register');

    // Validation helpers
    const emailEl = document.getElementById('email');
    const phoneEl = document.getElementById('phone');
    const pinEl = document.getElementById('pincode');
    const regSubmit = document.getElementById('regSubmit');

    const emailError = document.getElementById('emailError');
    const phoneError = document.getElementById('phoneError');
    const pinError = document.getElementById('pinError');

    function validateEmail(v) {
      // Simple email regex, good for demo
      return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(v);
    }
    function validatePhone(v) {
      return /^\d{10}$/.test(v);
    }
    function validatePin(v) {
      return /^\d{6}$/.test(v);
    }

    function openModal(title, message, onClose) {
      const modal = document.getElementById('modal');
      document.getElementById('modalTitle').textContent = title;
      document.getElementById('modalMessage').textContent = message;
      modal.classList.remove('hidden');
      modal.classList.add('flex');

      function close() {
        modal.classList.remove('flex');
        modal.classList.add('hidden');
        document.getElementById('modalClose').removeEventListener('click', close);
        if (onClose) onClose();
      }
      document.getElementById('modalClose').addEventListener('click', close);
    }

    // Real-time validation
    emailEl.addEventListener('input', () => {
      if (emailEl.value === '' || validateEmail(emailEl.value)) {
        emailError.classList.add('hidden');
      } else emailError.classList.remove('hidden');
    });
    phoneEl.addEventListener('input', () => {
      if (phoneEl.value === '' || validatePhone(phoneEl.value)) {
        phoneError.classList.add('hidden');
      } else phoneError.classList.remove('hidden');
    });
    pinEl.addEventListener('input', () => {
      if (pinEl.value === '' || validatePin(pinEl.value)) {
        pinError.classList.add('hidden');
      } else pinError.classList.remove('hidden');
    });

    regSubmit.addEventListener('click', () => {
      const emailOK = validateEmail(emailEl.value.trim());
      const phoneOK = validatePhone(phoneEl.value.trim());
      const pinOK = validatePin(pinEl.value.trim());

      if (!emailOK) emailError.classList.remove('hidden');
      if (!phoneOK) phoneError.classList.remove('hidden');
      if (!pinOK) pinError.classList.remove('hidden');

      if (emailOK && phoneOK && pinOK) {
        openModal('Registration Successful', 'Welcome to VoyageFlow! Preparing your travel content...', () => {
          // on modal close navigate to blog
          showPage('blog');
        });
        // auto-close modal after a short time and proceed
        setTimeout(() => {
          const btn = document.getElementById('modalClose');
          if (btn) btn.click();
        }, 1200);
      }
    });

    // Blog → Planner
    document.getElementById('toPlanner').addEventListener('click', () => showPage('planner'));

    // Planner: real-time calculation
    const checkboxes = Array.from(document.querySelectorAll('.optionCheckbox'));
    const totalEl = document.getElementById('totalPrice');
    const selectedList = document.getElementById('selectedList');

    function updateTotal() {
      let total = 0;
      const names = [];
      checkboxes.forEach(cb => {
        if (cb.checked) {
          total += Number(cb.dataset.price || 0);
          names.push(cb.dataset.name || 'Item');
        }
      });
      totalEl.textContent = total;
      selectedList.textContent = names.length ? names.join(', ') : 'None';
    }

    checkboxes.forEach(cb => cb.addEventListener('change', updateTotal));
    updateTotal();

    // Confirm plan
    document.getElementById('confirmPlan').addEventListener('click', () => {
      // Show confirmation modal summarizing selections
      const selected = checkboxes.filter(c => c.checked).map(c => ({ name: c.dataset.name, price: Number(c.dataset.price) }));
      if (selected.length === 0) {
        openModal('No selection', 'Please choose at least one option before confirming.');
        setTimeout(() => document.getElementById('modalClose').click(), 1000);
        return;
      }

      const sum = selected.reduce((s, it) => s + it.price, 0);
      const message = `You selected ${selected.length} item(s). Total: $${sum}. Proceeding to confirmation...`;
      openModal('Trip Confirmed', message, () => {
        // populate summary and show confirm page
        const summaryText = document.getElementById('summaryText');
        const lines = selected.map(it => `${it.name} — $${it.price}`);
        summaryText.innerHTML = `<strong>Items:</strong><br>${lines.join('<br>')}<br><strong>Total:</strong> $${sum}`;
        showPage('confirm');
      });
      setTimeout(() => document.getElementById('modalClose').click(), 1200);
    });

    document.getElementById('backToBlog').addEventListener('click', () => showPage('blog'));

    // Start over
    document.getElementById('startOver').addEventListener('click', () => {
      // reset everything
      document.getElementById('regForm').reset();
      document.getElementById('plannerForm').reset();
      updateTotal();
      showPage('register');
    });

    // Small accessibility: close modal on ESC
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') {
        const modal = document.getElementById('modal');
        if (!modal.classList.contains('hidden')) {
          const btn = document.getElementById('modalClose');
          if (btn) btn.click();
        }
      }
    });
  </script>
</body>
</html>
