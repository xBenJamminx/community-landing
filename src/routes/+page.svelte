<script lang="ts">
	import { onMount } from 'svelte';

	let openFaq = $state<number | null>(null);
	let mounted = $state(false);

	function toggleFaq(index: number) {
		openFaq = openFaq === index ? null : index;
	}

	onMount(() => {
		mounted = true;
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) entry.target.classList.add('visible');
				});
			},
			{ threshold: 0.1 }
		);
		document.querySelectorAll('.reveal').forEach((el) => observer.observe(el));
		return () => observer.disconnect();
	});

	const features = [
		{
			title: 'Guides + Breakdowns',
			desc: 'Written from real projects. Prompts, configs, steps. Not theory.',
			color: 'bg-cyan-light'
		},
		{
			title: 'Prompt Library',
			desc: 'Organized by use case. Each one tested and annotated.',
			color: 'bg-yellow-light'
		},
		{
			title: 'Template Vault',
			desc: 'Fork and use in minutes. Content pipelines, GTM kits, analysis frameworks.',
			color: 'bg-pink-light'
		},
		{
			title: 'GitHub Repos',
			desc: 'Members-only code you can fork and run. Starter kits, scripts, boilerplates.',
			color: 'bg-cyan-light'
		},
		{
			title: 'Tool Deals + Roundups',
			desc: 'Monthly honest assessments. Exclusive discounts. Designed to offset the membership.',
			color: 'bg-yellow-light'
		},
		{
			title: 'Chat, AMAs, Livestreams',
			desc: 'Daily founder presence. Monthly office hours. All recordings archived.',
			color: 'bg-pink-light'
		}
	];

	const faqs = [
		{
			q: 'Is this a course?',
			a: "No. It's a living library. New resources added regularly based on real work. No curriculum, no timeline. You get everything the moment you join."
		},
		{
			q: 'How is this different from free AI content?',
			a: 'Free content gives you the concept. This gives you the execution: actual prompts, exact configs, templates you can fork, and people to ask when you get stuck.'
		},
		{
			q: 'Do I need to be technical?',
			a: "No. If you can use Notion, Airtable, or a Chrome extension, you can use everything in here."
		},
		{
			q: 'Can I cancel anytime?',
			a: 'Yes. Monthly billing. No contracts. Founding pricing locked as long as you stay.'
		}
	];
</script>

<svelte:head>
	<title>BuildsByBen — AI for your whole life</title>
</svelte:head>

<!-- Nav -->
<nav class="fixed top-0 z-50 w-full border-b-3 border-ink bg-bg/90 backdrop-blur-md">
	<div class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4">
		<span class="font-display text-2xl font-bold text-ink">BuildsByBen</span>
		<a href="#founding" class="neo-btn rounded-lg bg-cyan px-5 py-2.5 text-sm text-ink">
			Join Now
		</a>
	</div>
</nav>

<!-- Hero -->
<section class="relative overflow-hidden pt-28 pb-16 md:pt-40 md:pb-24">
	<!-- Decorative shapes -->
	<div class="pointer-events-none absolute top-20 right-10 h-32 w-32 rotate-12 rounded-xl border-3 border-ink bg-yellow md:h-48 md:w-48" style="opacity: 0.4;"></div>
	<div class="pointer-events-none absolute bottom-10 left-10 h-24 w-24 -rotate-6 rounded-full border-3 border-ink bg-pink md:h-36 md:w-36" style="opacity: 0.3;"></div>

	<div class="relative mx-auto max-w-4xl px-6">
		<div class="{mounted ? 'reveal visible' : 'opacity-0'}">
			<div class="mb-6 inline-block rounded-lg border-3 border-ink bg-cyan px-4 py-1.5 font-mono text-xs font-medium uppercase tracking-wider text-ink shadow-[3px_3px_0_#000]">
				A living library for builders
			</div>
		</div>

		<h1 class="{mounted ? 'reveal visible' : 'opacity-0'} font-display text-5xl font-extrabold leading-[1.05] text-ink md:text-7xl lg:text-[5.5rem]">
			AI for your<br />whole life.
		</h1>

		<p class="{mounted ? 'reveal visible' : 'opacity-0'} mt-6 max-w-xl text-lg leading-relaxed text-muted md:text-xl">
			Guides, prompts, templates, repos, and a community of people using AI for work, family, side projects, and the stuff in between.
		</p>

		<div class="{mounted ? 'reveal visible' : 'opacity-0'} mt-10 flex flex-wrap items-center gap-4">
			<a href="#founding" class="neo-btn rounded-xl bg-cyan px-8 py-4 text-base text-ink">
				Become a founding member &rarr;
			</a>
			<span class="font-mono text-sm text-muted">50 spots &middot; $29/mo forever</span>
		</div>
	</div>
</section>

<!-- Scrolling marquee -->
<div class="overflow-hidden border-y-3 border-ink bg-ink py-3">
	<div class="animate-marquee flex w-max gap-8 whitespace-nowrap">
		{#each Array(2) as _}
			<span class="font-display text-lg font-bold text-bg">$300+ IN TEMPLATES</span>
			<span class="text-cyan">/</span>
			<span class="font-display text-lg font-bold text-bg">75+ LAUNCH DIRECTORIES</span>
			<span class="text-cyan">/</span>
			<span class="font-display text-lg font-bold text-bg">9 RESOURCE CATEGORIES</span>
			<span class="text-cyan">/</span>
			<span class="font-display text-lg font-bold text-bg">DAILY FOUNDER PRESENCE</span>
			<span class="text-cyan">/</span>
			<span class="font-display text-lg font-bold text-bg">CANCEL ANYTIME</span>
			<span class="text-cyan">/</span>
		{/each}
	</div>
</div>

<!-- Who This Is For -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-5xl px-6">
		<div class="reveal mx-auto max-w-3xl">
			<h2 class="font-display text-3xl font-bold leading-tight text-ink md:text-5xl">
				You know AI matters. You just don't have 6 hours to figure it out.
			</h2>
			<p class="mt-4 text-lg text-muted">
				This is for the person with a full-time job, a family, maybe a side project, and about 45 minutes after the kids go to bed.
			</p>
		</div>

		<div class="mt-14 grid gap-6 md:grid-cols-2">
			<div class="reveal neo-card rounded-2xl p-8">
				<h3 class="mb-5 font-display text-xl font-bold text-ink">This is for you if:</h3>
				<ul class="space-y-3">
					{#each [
						'A parent who wants to get more done so you can be present',
						'A full-time employee building on the side',
						'A small business owner who knows AI can help',
						'A freelancer or creator who wants practical shortcuts',
						'Someone who wants AI beyond chatbot conversations'
					] as item}
						<li class="flex gap-3 text-[0.95rem]">
							<span class="mt-0.5 flex h-6 w-6 shrink-0 items-center justify-center rounded-md border-2 border-ink bg-cyan-light text-sm font-bold">&#10003;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>

			<div class="reveal neo-card rounded-2xl p-8" style="transition-delay: 100ms;">
				<h3 class="mb-5 font-display text-xl font-bold text-ink">Not for you if:</h3>
				<ul class="space-y-3 text-muted">
					{#each [
						'Looking for a get-rich-quick AI hustle',
						'A dev who reads model papers for fun',
						'Expecting a course with start and end dates'
					] as item}
						<li class="flex gap-3 text-[0.95rem]">
							<span class="mt-0.5 flex h-6 w-6 shrink-0 items-center justify-center rounded-md border-2 border-ink/30 bg-pink-light text-sm font-bold text-ink/40">&#10007;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>
		</div>
	</div>
</section>

<!-- What You Get -->
<section class="border-y-3 border-ink bg-bg-alt py-20 md:py-28">
	<div class="mx-auto max-w-5xl px-6">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-ink md:text-5xl">
				What's inside.
			</h2>
			<p class="mt-3 text-lg text-muted">A growing library. A room full of people who use it.</p>
		</div>

		<div class="mt-12 grid gap-5 md:grid-cols-2 lg:grid-cols-3">
			{#each features as feature, i}
				<div
					class="reveal neo-card rounded-xl p-6"
					style="transition-delay: {i * 60}ms;"
				>
					<div class="mb-4 inline-block rounded-lg border-2 border-ink {feature.color} px-3 py-1 font-mono text-xs font-medium uppercase tracking-wider">
						0{i + 1}
					</div>
					<h3 class="text-lg font-bold text-ink">{feature.title}</h3>
					<p class="mt-2 text-sm leading-relaxed text-muted">{feature.desc}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Who Is Ben -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-4xl px-6">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-ink md:text-5xl">
				A dad, a worker, a builder. In that order.
			</h2>
		</div>

		<div class="reveal neo-card mt-10 rounded-2xl p-8 md:p-12">
			<p class="text-lg leading-relaxed text-ink md:text-xl">
				Ben is 37. Two young sons. Long Island. Works full-time at a tech startup. Runs a side consulting business doing AI automation for real companies. Builds products on nights and weekends.
			</p>
			<p class="mt-6 font-display text-2xl font-bold text-ink md:text-3xl">He uses AI for all of it.</p>
		</div>

		<div class="mt-6 grid gap-5 md:grid-cols-2">
			{#each [
				{ label: 'Clients', text: 'Document intelligence pipelines. AI-powered sites. Automation saving companies dozens of hours/week.', color: 'bg-cyan-light' },
				{ label: 'Family', text: 'Bedtime story generator. Activity idea engine. Birthday coordination app that replaced 47 text threads.', color: 'bg-yellow-light' },
				{ label: 'Internet', text: 'BookmarkIQ (Chrome extension). Retell (AI video repurposing). Open-source tools used by thousands.', color: 'bg-pink-light' },
				{ label: 'Fun', text: 'Hand-tracking particle system. AI search with spatial metaphors. An AI operator named Cortana running 24/7.', color: 'bg-cyan-light' }
			] as card, i}
				<div class="reveal neo-card rounded-xl p-6" style="transition-delay: {i * 60}ms;">
					<span class="inline-block rounded-md border-2 border-ink {card.color} px-3 py-1 font-mono text-xs font-medium uppercase tracking-wider">{card.label}</span>
					<p class="mt-3 text-sm leading-relaxed text-muted">{card.text}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Founding Members -->
<section id="founding" class="border-y-3 border-ink bg-ink py-20 md:py-28">
	<div class="mx-auto max-w-3xl px-6 text-center">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-bg md:text-5xl">
				50 founding spots.<br />$29/mo locked forever.
			</h2>
			<p class="mt-4 text-lg text-bg/60">
				After 50 founding members, the price goes to $49/mo. Founding price never changes.
			</p>
		</div>

		<div class="reveal mx-auto mt-12 max-w-sm" style="transition-delay: 150ms;">
			<div class="rounded-2xl border-3 border-bg bg-surface p-0 shadow-[8px_8px_0_theme(--color-cyan)]">
				<div class="border-b-3 border-ink bg-cyan px-8 py-6">
					<span class="font-mono text-sm font-bold uppercase tracking-widest text-ink">Founding Member</span>
					<div class="mt-3 flex items-baseline justify-center gap-1">
						<span class="font-display text-6xl font-extrabold text-ink">$29</span>
						<span class="text-xl text-ink/60">/mo</span>
					</div>
				</div>

				<div class="px-8 py-8">
					<ul class="space-y-3 text-left text-sm">
						{#each [
							'Permanent price lock at $29/mo',
							'Free lifetime access on future platforms',
							'Founding member badge',
							'Discounts on all future products',
							'Direct input on what gets built'
						] as perk}
							<li class="flex gap-3">
								<span class="mt-0.5 flex h-5 w-5 shrink-0 items-center justify-center rounded-md border-2 border-ink bg-cyan-light text-xs font-bold">&#10003;</span>
								{perk}
							</li>
						{/each}
					</ul>

					<a
						href="#founding"
						class="neo-btn mt-8 w-full justify-center rounded-xl bg-yellow px-6 py-4 text-base text-ink"
					>
						Lock in your spot &rarr;
					</a>
					<p class="mt-4 text-xs text-muted">Cancel anytime. No contracts.</p>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- FAQ -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-2xl px-6">
		<h2 class="reveal font-display text-3xl font-bold text-ink md:text-4xl">Questions</h2>

		<div class="mt-10 space-y-3">
			{#each faqs as faq, i}
				<div class="reveal" style="transition-delay: {i * 50}ms;">
					<button
						onclick={() => toggleFaq(i)}
						class="neo-card w-full rounded-xl px-6 py-5 text-left {openFaq === i ? 'bg-cyan-light' : ''}"
					>
						<div class="flex items-center justify-between">
							<span class="font-semibold text-ink">{faq.q}</span>
							<span class="ml-4 flex h-7 w-7 shrink-0 items-center justify-center rounded-md border-2 border-ink text-sm font-bold transition-all {openFaq === i ? 'rotate-45 bg-cyan' : 'bg-surface'}">+</span>
						</div>
					</button>
					<div class="faq-content {openFaq === i ? 'open' : ''}">
						<div>
							<p class="px-6 pt-3 pb-5 text-sm leading-relaxed text-muted">{faq.a}</p>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Final CTA -->
<section class="border-t-3 border-ink py-20 md:py-28">
	<div class="mx-auto max-w-3xl px-6 text-center">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-ink md:text-5xl">
				Real work. Real assets. Real community.
			</h2>
			<p class="mt-4 text-lg text-muted">
				50 spots. Full library. Partner perks. Direct access. $29/mo locked forever.
			</p>
			<a
				href="#founding"
				class="neo-btn mt-10 inline-flex rounded-xl bg-cyan px-8 py-4 text-base text-ink"
			>
				Become a founding member &rarr;
			</a>
		</div>
	</div>
</section>

<!-- Footer -->
<footer class="border-t-3 border-ink py-8">
	<div class="mx-auto flex max-w-6xl flex-col items-center gap-4 px-6 text-sm text-muted md:flex-row md:justify-between">
		<span class="font-bold text-ink">BuildsByBen &copy; {new Date().getFullYear()}</span>
		<div class="flex gap-6">
			<a href="https://x.com/xBenJamminx" target="_blank" rel="noopener" class="font-medium transition-colors hover:text-ink">X / Twitter</a>
			<a href="https://buildsbyben.com" target="_blank" rel="noopener" class="font-medium transition-colors hover:text-ink">Portfolio</a>
			<a href="https://github.com/xBenJamminx" target="_blank" rel="noopener" class="font-medium transition-colors hover:text-ink">GitHub</a>
		</div>
	</div>
</footer>
