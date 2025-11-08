<script lang="ts">
  import type { BuildInfo } from '$lib';

  export let buildInfo: BuildInfo;

  const hasBuildInfo = Boolean(
    buildInfo?.sha || buildInfo?.formattedTimestamp || (buildInfo?.showBranch && buildInfo?.branch)
  );

  const currentYear = new Date().getFullYear();
</script>

<footer class="footer">
  <div class="footer__content">
    <small>&copy; {currentYear} Template PWA Mobile</small>
    {#if hasBuildInfo}
      <small class="footer__meta">
        <span class="footer__meta-label">Build</span>
        {#if buildInfo.sha}
          <code>{buildInfo.sha}</code>
        {/if}
        {#if buildInfo.formattedTimestamp}
          <span>generated on {buildInfo.formattedTimestamp}</span>
        {/if}
        {#if buildInfo.showBranch && buildInfo.branch}
          <span>
            from the
            <code>{buildInfo.branch}</code>
            branch
          </span>
        {/if}
      </small>
    {/if}
  </div>
</footer>

<style>
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

  .footer__meta-label {
    text-transform: uppercase;
    letter-spacing: 0.08em;
    font-weight: 600;
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
</style>
