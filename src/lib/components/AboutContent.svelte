<script lang="ts">
  // No props needed for now as content is static
</script>

<div class="content-wrapper">
  <div class="text-container">
    <p class="mb-6">
      I'm Bo — a builder and problem solver with 20 years of experience designing, building, and scaling globally available SaaS and technology platforms. I've helped enterprises grow beyond 1B while also working hands-on with startups to turn ideas into real products. I'm an active founder myself and I've been through the wringer learning everything you shouldn't do as a first time founder.
    </p>
    <p>
      These days I'm passionate about making it easier for other founders to launch and grow their startups, especially in the Philadelphia region. My favorite part of the job is asking founders how I can help, then actually finding ways to make it happen. Outside of tech, I'm curious about philosophy, physics, and what drives the human experience and innovation. I'm also a cat dad, an uncle, a husband, and someone who loves life, travel, and always learning about the world.
    </p>
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

  @media (max-width: 768px) {
    .content-wrapper {
      padding: 1rem;
      min-height: min-content;
      height: auto;
      align-items: flex-start;
      overflow-y: auto;
    }

    .text-container {
      padding: 1.5rem;
      font-size: 1rem;
      margin: 1rem 0;
    }
  }
</style> 