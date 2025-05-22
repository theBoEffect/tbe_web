<script lang="ts">
  import { Globe, Linkedin } from 'lucide-svelte';
</script>

<div class="content-wrapper">
  <div class="text-container">
    <div class="mb-8">
      <p class="mb-6">
        United Effects® Ventures (UEV) is a Philly-based startup studio and incubator established by proven B2B technology leaders to offer origination-stage investment and support that derisks the earliest startup efforts, assuring young B2B technology companies start faster and go further.
      </p>
      <p class="mb-6">
        If you've heard "you're too early" or "call us when you hit $1m in revenue" one too many times, we feel your pain, and we built UEV for you.
      </p>
      <p class="mb-8">
        I'm so proud of the work we're doing at UEV with our portfolio companies and with the community as a whole. Find out more by visiting our site or Linkedin!
      </p>
    </div>
    <div class="flex items-center justify-center gap-8">
      <a 
        href="https://ue.ventures" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link"
        aria-label="Visit UEV Website"
      >
        <Globe class="w-8 h-8" />
      </a>
      <a 
        href="https://www.linkedin.com/company/ue-ventures" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link"
        aria-label="Visit UEV LinkedIn Profile"
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