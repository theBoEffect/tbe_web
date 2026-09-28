<script lang="ts">
  import { Globe, Linkedin } from 'lucide-svelte';
</script>

<div class="content-wrapper">
  <div class="text-container">
    <div class="mb-8">
      <p class="mb-6">
        United Effects has been my brand across three companies. It began as a bunch of ideas about how amazing people united can build amazing things, scribbled into a notebook in a coffee shop in 2016. It became an enterprise SaaS company where I designed, built, and launched two products, in identity security and data streaming, and wrote the two patents that came out of that architecture.
      </p>
      <p class="mb-6">
        It grew into a venture chapter: a small fund, a portfolio, and a lot of time alongside early-stage founders in the Philadelphia region. I learned more there about what founders actually need than anywhere else.
      </p>
      <p class="mb-8">
        Today it's United Effects Labs, an operator-led AI venture studio. We launch ventures, embed with enterprises to ship real AI, and accelerate founders. It's the work I'm proudest of. Find out more by visiting our site or LinkedIn!
      </p>
    </div>
    <div class="flex items-center justify-center gap-8">
      <a 
        href="https://uelabs.ai" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link"
        aria-label="Visit United Effects Labs Website"
      >
        <Globe class="w-8 h-8" />
      </a>
      <a 
        href="https://www.linkedin.com/company/uelabs" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link"
        aria-label="Visit United Effects Labs LinkedIn Page"
      >
        <Linkedin class="w-8 h-8" />
      </a>
    </div>
  </div>
</div>

<style>
  .content-wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem;
  }

  .text-container {
    background-color: rgba(0, 0, 0, 0.6);
    padding: 2rem;
    border-radius: 0.5rem;
    max-width: 800px;
    width: 100%;
    color: white;
    font-size: 1.125rem;
    line-height: 1.75;
    backdrop-filter: blur(4px);
  }

  .social-link {
    color: white;
    transition: all 0.3s ease-in-out;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .social-link:hover {
    transform: scale(1.1);
    color: #ff0054;
  }

  /* Desktop-specific positioning */
  @media (min-width: 769px) {
    .content-wrapper {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      margin: auto;
    }

    .text-container {
      margin-top: 25px;
    }
  }

  /* Mobile-specific positioning */
  @media (max-width: 768px) {
    .content-wrapper {
      height: 100%;
      padding: 1rem;
      position: static;
      overflow-y: auto;
      display: block;
    }

    .text-container {
      padding: 1.5rem;
      font-size: 1rem;
      width: 100%;
      margin: 1rem auto;
      max-height: none;
    }
  }
</style> 