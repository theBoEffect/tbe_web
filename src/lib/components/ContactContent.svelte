<script lang="ts">
  import { Linkedin } from 'lucide-svelte';
</script>

<div class="content-wrapper">
  <div class="text-container">
    <div class="profile-section">
      <img src="/bo.jpeg" alt="Bo Motlagh" class="profile-image" />
      <p class="message mb-6">
        If you're trying to get in touch, please reach out through a LinkedIn message and I'm happy to say hello!
      </p>
    </div>
    <div class="flex items-center justify-center">
      <a 
        href="https://www.linkedin.com/in/bmotlagh/" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link"
        aria-label="Visit Bo's LinkedIn Profile"
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

  .profile-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
    margin-bottom: 1.5rem;
  }

  .profile-image {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid white;
  }

  .message {
    text-align: center;
    max-width: 500px;
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

    .profile-image {
      width: 150px;
      height: 150px;
    }
  }
</style> 