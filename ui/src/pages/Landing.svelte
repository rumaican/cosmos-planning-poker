<script lang="ts">
  import { AppConfig, appRoutes } from '../config';
  import { user } from '../stores';
  import { Github, Users, Zap } from 'lucide-svelte';
  import LL from '../i18n/i18n-svelte';
  import Countries from '../components/user/Countries.svelte';
  import BrowserMock from '../components/global/BrowserMock.svelte';
  import { onMount } from 'svelte';
  import type { ApiClient } from '../types/apiclient';

  interface Props {
    xfetch: ApiClient;
  }

  let { xfetch }: Props = $props();

  const { ShowActiveCountries, PathPrefix, RepoURL } = AppConfig;





  onMount(() => window.scrollTo(0, 0));
</script>

<svelte:head>
  <title>{$LL.appName()} - {$LL.appSubtitle()}</title>
</svelte:head>

<main class="bg-gray-100 dark:bg-gray-900">
  <header class="bg-gradient-to-r from-blue-600 to-indigo-700 text-white">
    <div class="container mx-auto px-4 py-16">
      <div class="max-w-7xl mx-auto text-center">
        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-bold mb-6 leading-tight">
          Team <span class="text-yellow-thunder">Cosmos</span>, Aligned
        </h1>
        <p class="max-w-4xl mx-auto text-xl sm:text-2xl text-white/80 mb-8">
          Clear estimates. Honest retros. Forward momentum.
        </p>
        <div class="flex flex-col sm:flex-row items-center justify-center space-y-4 sm:space-y-0 sm:space-x-6">
          {#if $user.id}
            <a
              href={appRoutes.games}
              class="bg-white text-indigo-700 hover:bg-gray-100 font-semibold py-3 px-8 rounded-full transition duration-300 shadow-lg"
            >
              Start Planning
            </a>
          {:else}
            <a
              href={appRoutes.register}
              class="bg-white text-indigo-700 hover:bg-gray-100 font-semibold py-3 px-8 rounded-full transition duration-300 shadow-lg"
            >
              Get Started Free
            </a>
          {/if}
          <a
            href="#features"
            class="bg-transparent text-white hover:bg-white/10 border border-white font-semibold py-3 px-8 rounded-full transition duration-300"
          >
            Explore Features
          </a>
        </div>
      </div>
    </div>
  </header>

  <section id="features" class="bg-white dark:bg-gray-800 py-20">
    <div class="container mx-auto px-4">
      <div class="flex flex-col md:flex-row items-center justify-between">
        <div class="md:w-1/2 md:pe-8 mb-8 md:mb-0">
          <div class="title-line bg-yellow-thunder"></div>
          <h2 class="text-4xl font-semibold font-rajdhani uppercase dark:text-white mb-6">
            Planning Poker for Accurate Estimation
          </h2>
          <p class="text-lg text-gray-600 dark:text-gray-400 mb-4">
            Estimate story points with the whole team using anonymous voting to eliminate bias and surface honest assessments.
          </p>
          <ul class="space-y-3 text-gray-700 dark:text-gray-300 mb-8">
            <li class="flex items-start">
              <span class="text-indigo-500 dark:text-indigo-400 me-2">✓</span>
              <span><strong>Eliminate estimation bias:</strong> Anonymous voting prevents anchoring and groupthink</span
              >
            </li>
            <li class="flex items-start">
              <span class="text-indigo-500 dark:text-indigo-400 me-2">✓</span>
              <span
                ><strong>Flexible scales:</strong> Use Fibonacci, T-shirt sizes, or create custom ranges that fit your workflow</span
              >
            </li>
            <li class="flex items-start">
              <span class="text-indigo-500 dark:text-indigo-400 me-2">✓</span>
              <span
                ><strong>Remote-first design:</strong> Equal participation whether you're in-person or distributed</span
              >
            </li>
          </ul>
          <a
            href={appRoutes.games}
            class="group relative inline-flex items-center justify-center p-0.5 mb-2 me-2 overflow-hidden font-medium text-gray-900 rounded-lg group bg-gradient-to-br from-purple-600 to-blue-500 group-hover:from-purple-600 group-hover:to-blue-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800"
          >
            <span
              class="relative px-5 py-2.5 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-md group-hover:bg-opacity-0"
            >
              {$user.id ? $LL.battleCreate() : 'Try Planning Poker'}
            </span>
          </a>
        </div>
        <div class="md:w-1/2">
          <BrowserMock>
            <img
              class="rounded-b-lg hidden dark:block"
              src="{PathPrefix}/img/previews/planning_poker_20250812_dark.png"
              alt={$LL.appPreviewAlt()}
            />
            <img
              class="rounded-b-lg dark:hidden"
              src="{PathPrefix}/img/previews/planning_poker_20250812_light.png"
              alt={$LL.appPreviewAlt()}
            />
          </BrowserMock>
        </div>
      </div>
    </div>
  </section>

  <section class="bg-gray-100 dark:bg-gray-900 py-20">
    <div class="container mx-auto px-4">
      <div class="flex flex-col md:flex-row-reverse items-center justify-between">
        <div class="md:w-1/2 md:ps-8 mb-8 md:mb-0">
          <div class="title-line bg-yellow-thunder"></div>
          <h2 class="text-4xl font-semibold font-rajdhani uppercase dark:text-white mb-6">
            Retrospectives for Team Improvement
          </h2>
          <p class="text-lg text-gray-600 dark:text-gray-400 mb-4">
            Foster honest feedback and actionable outcomes. Built for Cosmos to support continuous improvement through structured retrospectives.
          </p>
          <ul class="space-y-3 text-gray-700 dark:text-gray-300 mb-8">
            <li class="flex items-start">
              <span class="text-indigo-500 dark:text-indigo-400 me-2">✓</span>
              <span
                ><strong>Battle-tested formats:</strong> Start/Stop/Continue, 4Ls, Mad/Sad/Glad, plus custom templates</span
              >
            </li>
            <li class="flex items-start">
              <span class="text-indigo-500 dark:text-indigo-400 me-2">✓</span>
              <span
                ><strong>Safe space for honesty:</strong> Anonymous feedback removes fear of judgment or retaliation</span
              >
            </li>
            <li class="flex items-start">
              <span class="text-indigo-500 dark:text-indigo-400 me-2">✓</span>
              <span
                ><strong>Accountability that works:</strong> Convert insights into trackable action items with follow-through</span
              >
            </li>
          </ul>
          <a
            href={appRoutes.retros}
            class="group relative inline-flex items-center justify-center p-0.5 mb-2 me-2 overflow-hidden font-medium text-gray-900 rounded-lg group bg-gradient-to-br from-purple-600 to-blue-500 group-hover:from-purple-600 group-hover:to-blue-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800"
          >
            <span
              class="relative px-5 py-2.5 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-md group-hover:bg-opacity-0"
            >
              {$user.id ? 'Start a Retrospective' : 'Try Retrospectives'}
            </span>
          </a>
        </div>
        <div class="md:w-1/2">
          <BrowserMock>
            <img
              class="rounded-b-lg hidden dark:block"
              src="{PathPrefix}/img/previews/retro_20250812_dark.png"
              alt="Sprint Retrospectives Preview"
            />
            <img
              class="rounded-b-lg dark:hidden"
              src="{PathPrefix}/img/previews/retro_20250812_light.png"
              alt="Sprint Retrospectives Preview"
            />
          </BrowserMock>
        </div>
      </div>
    </div>
  </section>



  <!-- Placeholder section for future tools -->
  <section class="bg-gray-100 dark:bg-gray-900 py-20">
    <div class="container mx-auto px-4">
      <div class="flex flex-col md:flex-row-reverse items-center justify-between">
        <div class="md:w-1/2 md:ps-8 mb-8 md:mb-0">
          <div class="title-line bg-yellow-thunder"></div>
          <h2 class="text-4xl font-semibold font-rajdhani uppercase dark:text-white mb-6">Additional Tools Coming Soon</h2>
          <p class="text-lg text-gray-600 dark:text-gray-400 mb-8">
            Stay tuned for additional team collaboration tools.
          </p>
        </div>
        <div class="md:w-1/2">
          <img
            class="rounded-lg shadow-lg hidden dark:block max-w-lg mx-auto"
            src="{PathPrefix}/img/previews/team_checkins_dark_2025_09_24.png"
            alt="Team Checkins Preview"
          />
          <img
            class="rounded-lg shadow-lg dark:hidden max-w-lg mx-auto"
            src="{PathPrefix}/img/previews/team_checkins_light_2025_09_24.png"
            alt="Team Checkins Preview"
          />
        </div>
      </div>
    </div>
  </section>

  <section class="bg-indigo-600 text-white py-20">
    <div class="container mx-auto px-4 text-center">
      <h2 class="text-4xl font-bold mb-6 font-rajdhani uppercase">Why Cosmos Uses This Tool</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div class="bg-white dark:bg-gray-800 rounded-lg p-6 text-gray-800 dark:text-white">
          <div class="text-indigo-500 text-4xl mb-4">
            <Zap class="h-12 w-12 mx-auto" />
          </div>
          <h3 class="text-xl font-semibold mb-2">Team Alignment</h3>
          <p>
            Everyone contributes to estimation and retrospectives, ensuring shared understanding across our distributed team.
          </p>
        </div>
        <div class="bg-white dark:bg-gray-800 rounded-lg p-6 text-gray-800 dark:text-white">
          <div class="text-indigo-500 text-4xl mb-4">
            <Users class="h-12 w-12 mx-auto" />
          </div>
          <h3 class="text-xl font-semibold mb-2">Consistent Process</h3>
          <p>
            Standardized tools for planning poker and retros keep our ceremonies structured and productive.
          </p>
        </div>
        <div class="bg-white dark:bg-gray-800 rounded-lg p-6 text-gray-800 dark:text-white">
          <div class="text-indigo-500 text-4xl mb-4">
            <Github class="h-12 w-12 mx-auto" />
          </div>
          <h3 class="text-xl font-semibold mb-2">Shared Understanding</h3>
          <p>
            Real-time collaboration tools help Cosmos maintain clarity and transparency across all sprint activities.
          </p>
        </div>
      </div>
    </div>
  </section>

  {#if ShowActiveCountries}
    <section class="bg-slate-100 dark:bg-gray-900 py-20">
      <div class="container mx-auto px-4">
        <Countries {xfetch} />
      </div>
    </section>
  {/if}
</main>
