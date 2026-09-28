<script lang="ts">
  interface NewsStory {
    title: string;
    excerpt: string;
    imageUrl: string;
    link: string;
    source: string;
    date: string;
    useLogoStyle?: boolean;  // Flag to determine if we should use logo styling
  }

  const newsStories: NewsStory[] = [
    {
      title: "UnitedEffect's Motlagh is Redesigning the Notion of Enterprise Software",
      excerpt: "The first piece anyone wrote about United Effects, in the very early days of the journey, on why enterprise software doesn't have to be ugly.",
      imageUrl: "/bo.jpeg",
      link: "https://medium.com/strtupboost/bo-motlagh-is-redesigning-the-notion-of-enterprise-software-30f560d6d30e",
      source: "SuperWarm on Medium",
      date: "Aug 12, 2021",
      useLogoStyle: false
    },
    {
      title: "United Effects Ventures Debuts as Philadelphia-Focused B2B Startup Studio & Incubator",
      excerpt: "The venture chapter begins: a Philadelphia studio and fund for B2B founders at their earliest steps.",
      imageUrl: "/uev.png",
      link: "https://www.prweb.com/releases/united-effects-ventures-debuts-as-philadelphia-focused-b2b-startup-studio--incubator-302459675.html",
      source: "PRWeb",
      date: "May 20, 2025",
      useLogoStyle: true
    },
    {
      title: "Got a startup idea? This new Philly venture studio wants to find founders at their earliest steps",
      excerpt: "Technical.ly on the launch and the plan to rebuild the region's founder community.",
      imageUrl: "/backgrounds/ww.jpeg",
      link: "https://technical.ly/startups/philadelphia-united-effects-ventures-studio-launch/",
      source: "Technical.ly",
      date: "May 20, 2025",
      useLogoStyle: false
    },
    {
      title: "Venture studios promise hands-on startup building. Here's how they work.",
      excerpt: "A look at how venture studios work, and the relationship-first model I described: not a check, but working alongside founders.",
      imageUrl: "/news/technically-venture-studios-2026.jpg",
      link: "https://technical.ly/entrepreneurship/startup-funding-support-venture-studios-explained/",
      source: "Technical.ly",
      date: "Apr 21, 2026",
      useLogoStyle: false
    },
    {
      title: "United Effects Ventures Evolution: Bo Motlagh to Lead UE Labs",
      excerpt: "The studio evolves, and United Effects Labs takes on the build: launching ventures, embedding with enterprises, and accelerating founders.",
      imageUrl: "/uel-logo.png",
      link: "https://www.publicnow.com/view/BA6B8ECE8F3E169FE87209617EDCDEE8E666E596",
      source: "Press Release",
      date: "Jun 1, 2026",
      useLogoStyle: true
    },
    {
      title: "About United Effects Labs",
      excerpt: "Where it stands today: an operator-led AI venture studio that launches new ventures, embeds with enterprises to ship real AI, and accelerates early-stage founders.",
      imageUrl: "/uel-logo2.png",
      link: "https://uelabs.ai/about",
      source: "uelabs.ai",
      date: "Today",
      useLogoStyle: true
    }
  ];
</script>

<div class="content-wrapper">
  <div class="text-container">
    <div class="news-grid">
      {#each newsStories as story}
        <a 
          href={story.link}
          target="_blank"
          rel="noopener noreferrer"
          class="news-card"
        >
          <div class="news-image-container">
            {#if story.useLogoStyle}
              <div class="image-overlay"></div>
              <img 
                src={story.imageUrl} 
                alt={story.title}
                class="w-full h-full object-contain p-8"
              />
            {:else}
              <img 
                src={story.imageUrl} 
                alt={story.title}
                class="w-full h-full object-cover"
              />
            {/if}
          </div>
          <div class="p-4">
            <div class="flex justify-between items-center mb-2 text-sm opacity-80">
              <span>{story.source}</span>
              <span>{story.date}</span>
            </div>
            <h3 class="text-base font-bold mb-2">{story.title}</h3>
            <p class="text-sm opacity-90">{story.excerpt}</p>
          </div>
        </a>
      {/each}
    </div>
  </div>
</div>

<style>
  /* Desktop styles */
  .content-wrapper {
    width: 100%;
    min-height: 100%;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 2rem;
  }

  .text-container {
    background-color: rgba(0, 0, 0, 0.6);
    padding: 1.5rem;
    border-radius: 0.5rem;
    max-width: 1200px;
    color: white;
    font-size: 1rem;
    line-height: 1.6;
    backdrop-filter: blur(4px);
    width: 100%;
  }

  .news-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  @media screen and (max-width: 1100px) {
    .news-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  .news-card {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 0.5rem;
    overflow: hidden;
    transition: all 0.3s ease-in-out;
    display: flex;
    flex-direction: column;
  }

  .news-card:hover {
    transform: translateY(-4px);
    background-color: rgba(255, 255, 255, 0.15);
  }

  .news-image-container {
    position: relative;
    padding-top: 56.25%; /* 16:9 aspect ratio */
    overflow: hidden;
    background-color: #000000;
  }

  .image-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(45deg, rgba(0, 246, 255, 0.1), rgba(255, 0, 84, 0.1));
    z-index: 1;
  }

  .news-image-container img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
  }

  /* Mobile styles */
  @media screen and (max-width: 768px) {
    .content-wrapper {
      padding: 1rem;
      height: auto;
      min-height: auto;
      align-items: flex-start;
    }

    .text-container {
      padding: 1.5rem;
      font-size: 1rem;
      margin: 1rem 0;
    }

    .news-grid {
      grid-template-columns: 1fr;
      gap: 1rem;
    }

    .news-card {
      margin-bottom: 1rem;
    }

    .news-image-container {
      padding-top: 66.67%; /* 3:2 aspect ratio for mobile */
    }
  }
</style> 