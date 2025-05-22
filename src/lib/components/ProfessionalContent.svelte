<script lang="ts">
  // Import icons from an icon library (we'll need to add this to the project)
  import { Linkedin, Github } from 'lucide-svelte';
</script>

<div class="content-wrapper">
  <div class="text-container">
    <p class="mb-8">
      I've had a long career with some amazing experiences. I've also coded up some interesting things over the years. The easiest way to explore is to check my linkedin and my github accounts. See the links below!
    </p>
    <div class="flex items-center justify-center gap-8">
      <a 
        href="https://www.linkedin.com/in/bmotlagh/" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link"
        aria-label="Visit Bo's LinkedIn Profile"
      >
        <Linkedin class="w-8 h-8" />
      </a>
      <a 
        href="https://github.com/theboeffect" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link"
        aria-label="Visit Bo's Personal GitHub Profile"
      >
        <Github class="w-8 h-8" />
      </a>
      <a 
        href="https://github.com/UnitedEffects" 
        target="_blank" 
        rel="noopener noreferrer"
        class="social-link ue-github"
        aria-label="Visit United Effects GitHub Profile"
      >
        <Github class="w-8 h-8" />
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

  .ue-github {
    color: #ff0054;
  }

  .ue-github:hover {
    color: white;
  }

  @media (max-width: 768px) {
    .content-wrapper {
      padding: 1rem;
    }

    .text-container {
      padding: 1.5rem;
      font-size: 1rem;
    }
  }
</style> 