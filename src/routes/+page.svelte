<script lang="ts">
  import { buildInfo } from '$lib';

  const hasBuildInfo = Boolean(
    buildInfo.sha || buildInfo.formattedTimestamp || (buildInfo.showBranch && buildInfo.branch)
  );
</script>

<svelte:head>
  <title>Template PWA Mobile</title>
  <meta
    name="description"
    content="A mobile-first SvelteKit Progressive Web App starter ready for GitHub Pages deployments."
  />
</svelte:head>

<main class="page">
  <section class="hero">
    <p class="eyebrow">Progressive Web App template</p>
    <h1>Build mobile experiences that ship fast.</h1>
    <p class="lead">
      Kick-start your next project with an opinionated SvelteKit setup featuring offline support,
      responsive defaults, and an automated GitHub Pages workflow.
    </p>
    <div class="cta-row">
      <a class="button" href="https://kit.svelte.dev/docs" rel="noreferrer" target="_blank">
        Explore SvelteKit docs
      </a>
      <a class="ghost" href="https://github.com/features/actions" target="_blank" rel="noreferrer">
        Learn about GitHub Actions
      </a>
    </div>
  </section>

  <section class="grid">
    <article>
      <h2>Mobile-first defaults</h2>
      <p>
        Layouts are optimised for small screens out of the box, making it easy to deliver great
        experiences on any device.
      </p>
    </article>
    <article>
      <h2>Offline ready</h2>
      <p>
        A lightweight service worker caches your application shell so people can re-open it even
        when the network drops.
      </p>
    </article>
    <article>
      <h2>Automated deployments</h2>
      <p>
        Ship to GitHub Pages directly from Actions with branch-specific previews and environment
        metadata baked into the build.
      </p>
    </article>
  </section>
</main>

<footer class="footer">
  <div class="footer__content">
    <small>&copy; {new Date().getFullYear()} Template PWA Mobile</small>
    {#if hasBuildInfo}
      <small class="footer__meta">
        <span>build</span>
        {#if buildInfo.sha}
          <code>{buildInfo.sha}</code>
        {/if}
        {#if buildInfo.formattedTimestamp}
          <span>on {buildInfo.formattedTimestamp}</span>
        {/if}
        {#if buildInfo.showBranch && buildInfo.branch}
          <span>
            from branch
            <code>{buildInfo.branch}</code>
          </span>
        {/if}
      </small>
    {/if}
  </div>
</footer>

<style>
  .page {
    padding: clamp(1.5rem, 4vw, 3rem);
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: clamp(2.5rem, 6vw, 4rem);
  }

  .hero {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    text-align: left;
  }

  .eyebrow {
    font-size: 0.75rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    font-weight: 600;
    color: #2563eb;
  }

  h1 {
    font-size: clamp(2.2rem, 6vw, 3.5rem);
    line-height: 1.05;
    margin: 0;
  }

  .lead {
    font-size: 1rem;
    line-height: 1.6;
    max-width: 38rem;
    margin: 0;
  }

  .cta-row {
    display: flex;
    flex-wrap: wrap;
    gap: 0.75rem;
  }

  .button,
  .ghost {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border-radius: 999px;
    padding: 0.75rem 1.5rem;
    font-weight: 600;
    text-decoration: none;
    transition:
      transform 0.15s ease,
      box-shadow 0.15s ease;
  }

  .button {
    background: linear-gradient(135deg, #2563eb, #1d4ed8);
    color: white;
    box-shadow: 0 10px 25px rgba(37, 99, 235, 0.2);
  }

  .ghost {
    border: 1px solid rgba(37, 99, 235, 0.4);
    color: #1d4ed8;
    background: rgba(255, 255, 255, 0.7);
  }

  .button:hover,
  .ghost:hover {
    transform: translateY(-1px);
    box-shadow: 0 12px 30px rgba(15, 23, 42, 0.12);
  }

  .grid {
    display: grid;
    gap: 1.5rem;
  }

  .grid article {
    background: white;
    border-radius: 1rem;
    padding: 1.5rem;
    box-shadow: 0 20px 45px rgba(15, 23, 42, 0.08);
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .grid h2 {
    margin: 0;
    font-size: 1.25rem;
  }

  .grid p {
    margin: 0;
    line-height: 1.5;
    color: #1f2937;
  }

  .footer {
    padding: 1.5rem clamp(1.5rem, 4vw, 3rem);
    text-align: center;
    background: transparent;
    color: rgba(15, 23, 42, 0.7);
    border-top: 1px solid rgba(148, 163, 184, 0.3);
  }

  .footer__content {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    align-items: center;
    justify-content: center;
  }

  .footer__meta {
    display: flex;
    flex-wrap: wrap;
    gap: 0.25rem 0.5rem;
    align-items: center;
    justify-content: center;
  }

  .footer__meta code {
    background: rgba(15, 23, 42, 0.08);
    border-radius: 0.375rem;
    padding: 0.1rem 0.35rem;
    font-family:
      'JetBrains Mono', 'SFMono-Regular', Menlo, Monaco, Consolas, 'Liberation Mono', 'Courier New',
      monospace;
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  @media (min-width: 48rem) {
    .grid {
      grid-template-columns: repeat(3, minmax(0, 1fr));
    }
  }
</style>
