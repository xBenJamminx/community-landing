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
					if (entry.isIntersecting) {
						entry.target.classList.add('visible');
					}
				});
			},
			{ threshold: 0.1, rootMargin: '0px 0px -40px 0px' }
		);

		document.querySelectorAll('.reveal').forEach((el) => observer.observe(el));

		return () => observer.disconnect();
	});

	const features = [
		{
			label: 'Library',
			title: 'Guides and Breakdowns',
			desc: 'Written from real projects. How-tos, build breakdowns, tool deep dives, workflow walkthroughs. Every guide includes the prompts, configs, and steps to actually do the thing yourself.'
		},
		{
			label: 'Prompts',
			title: 'Prompt Library',
			desc: 'Organized by category: content creation, research, product planning, client work, model optimization. Each prompt includes context on when to use it and which model works best.'
		},
		{
			label: 'Templates',
			title: 'Template Vault',
			desc: 'Plug-and-play systems you can fork. Content Pipeline, GTM Launch Kit (75+ directories), Product Spec Template, Competitive Analysis Framework, and more added regularly.'
		},
		{
			label: 'Code',
			title: 'GitHub Repos',
			desc: 'Members-only repositories you can fork and run. Starter kits, automation scripts, boilerplates. Not toy demos. Functional code you can build on.'
		},
		{
			label: 'Curation',
			title: 'Roundups and Deals',
			desc: 'Monthly "best AI tools" roundup with honest assessments. Model comparisons when new releases drop. Exclusive tool discounts designed to offset the membership cost entirely.'
		},
		{
			label: 'Community',
			title: 'Chat, Livestreams, AMAs',
			desc: 'Topic channels for tools, building, wins, help, and off-topic. Build sessions, monthly AMAs, office hours. All recordings stay in the community.'
		}
	];

	const faqs = [
		{
			q: 'Is this a course?',
			a: "No. It's a living library and community. New guides, prompts, templates, and repos are added regularly based on real work. No curriculum, no start date, no end date. You get access to everything the moment you join."
		},
		{
			q: 'How is this different from free AI content?',
			a: 'Free content gives you the concept. The community gives you the execution. The actual prompts, the exact configs, the step-by-step walkthroughs, the templates you can fork, and the support to get unstuck.'
		},
		{
			q: 'Do I need to be technical?',
			a: "No. Most guides are written for people who are comfortable using apps and tools but aren't developers. If you can use Notion, Airtable, or a Chrome extension, you can use what's in here."
		},
		{
			q: "How much of Ben's time goes into this?",
			a: "Ben is in the community daily. Responds to questions, shares what he's working on, drops resources as he builds them. Monthly AMAs and livestreams on a regular cadence."
		},
		{
			q: 'Can I cancel anytime?',
			a: 'Yes. Monthly billing, cancel whenever. No contracts. Founding member pricing is locked as long as you stay subscribed.'
		}
	];
</script>

<svelte:head>
	<title>BuildsByBen — AI for your whole life</title>
</svelte:head>

<!-- Nav -->
<nav class="fixed top-0 z-50 w-full bg-midnight/60 backdrop-blur-2xl">
	<div class="mx-auto flex max-w-6xl items-center justify-between px-6 py-5">
		<span class="font-display text-xl font-bold tracking-tight text-heading">Builds<span class="text-accent">By</span>Ben</span>
		<a
			href="#founding"
			class="rounded-lg bg-accent px-5 py-2.5 text-sm font-semibold text-midnight transition-all duration-300 hover:bg-accent-light hover:shadow-lg hover:shadow-accent/20"
		>
			Join Now
		</a>
	</div>
</nav>

<!-- Hero -->
<section class="relative min-h-screen flex items-center justify-center overflow-hidden">
	<!-- Background glow -->
	<div class="pointer-events-none absolute inset-0">
		<div class="animate-glow-pulse absolute top-1/4 left-1/3 h-[500px] w-[500px] rounded-full bg-accent/8 blur-[120px]"></div>
		<div class="animate-glow-pulse absolute right-1/4 bottom-1/3 h-[400px] w-[400px] rounded-full bg-accent-glow/6 blur-[100px]" style="animation-delay: 2.5s;"></div>
	</div>

	<div class="relative mx-auto max-w-5xl px-6 pt-32 pb-24 text-center">
		<div class="{mounted ? 'animate-fade-up' : 'opacity-0'}">
			<span class="label-mono">A living library for builders</span>
		</div>

		<h1 class="{mounted ? 'animate-fade-up delay-100' : 'opacity-0'} mt-8 font-display text-5xl font-extrabold leading-[1.05] tracking-tight text-heading md:text-7xl lg:text-8xl">
			AI for your<br />
			<span class="text-gradient">whole life.</span>
		</h1>

		<p class="{mounted ? 'animate-fade-up delay-200' : 'opacity-0'} mx-auto mt-8 max-w-xl text-lg leading-relaxed text-muted md:text-xl">
			Guides, prompts, templates, repos, and a community of people using AI for work, family, side projects, and the stuff in between.
		</p>

		<div class="{mounted ? 'animate-fade-up delay-300' : 'opacity-0'} mt-12 flex flex-col items-center gap-4">
			<a
				href="#founding"
				class="group inline-flex items-center rounded-lg bg-accent px-8 py-4 text-base font-semibold text-midnight transition-all duration-300 hover:bg-accent-light hover:shadow-xl hover:shadow-accent/20"
			>
				Become a founding member
				<span class="ml-2 transition-transform duration-300 group-hover:translate-x-1">&rarr;</span>
			</a>
			<span class="font-mono text-xs tracking-wide text-muted/60">50 spots. $29/mo locked forever.</span>
		</div>
	</div>
</section>

<!-- Shimmer divider -->
<div class="shimmer-line"></div>

<!-- Numbers -->
<section class="py-20 md:py-28">
	<div class="mx-auto grid max-w-4xl grid-cols-2 gap-8 px-6 md:grid-cols-4">
		{#each [
			{ num: '$300+', label: 'in templates' },
			{ num: '75+', label: 'launch directories' },
			{ num: '9', label: 'resource categories' },
			{ num: 'Daily', label: 'founder presence' }
		] as stat, i}
			<div class="reveal text-center" style="transition-delay: {i * 100}ms;">
				<div class="font-display text-3xl font-bold text-heading md:text-4xl">{stat.num}</div>
				<div class="mt-2 text-sm text-muted">{stat.label}</div>
			</div>
		{/each}
	</div>
</section>

<!-- Who This Is For -->
<section class="py-20 md:py-32">
	<div class="mx-auto max-w-5xl px-6">
		<div class="reveal mx-auto max-w-3xl text-center">
			<span class="label-mono">Who this is for</span>
			<h2 class="mt-6 font-display text-3xl font-bold leading-tight text-heading md:text-5xl lg:text-6xl">
				You know AI matters. You just don't have <span class="text-gradient">6 hours to figure it out.</span>
			</h2>
		</div>

		<div class="mt-20 grid gap-6 md:grid-cols-2">
			<div class="reveal card-elevated rounded-2xl p-8 md:p-10">
				<span class="label-mono">This is for you</span>
				<ul class="mt-6 space-y-4 text-text">
					{#each [
						'A parent who wants to get more done so you can actually be present',
						'A full-time employee building something on the side',
						'A small business owner who knows AI can help but doesn\'t know where to start',
						'A freelancer, creator, or marketer who wants practical shortcuts',
						'Someone who wants to use AI beyond basic chatbot conversations'
					] as item}
						<li class="flex gap-3 text-[0.95rem] leading-relaxed">
							<span class="mt-1 flex h-5 w-5 shrink-0 items-center justify-center rounded-full bg-accent/10 text-xs text-accent">&#10003;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>

			<div class="reveal card-elevated rounded-2xl p-8 md:p-10" style="transition-delay: 150ms;">
				<span class="label-mono" style="color: var(--color-muted);">Not for you</span>
				<ul class="mt-6 space-y-4 text-muted">
					{#each [
						'Looking for a get-rich-quick AI hustle community',
						'A developer who already lives in VS Code and reads model papers for fun',
						'Expecting a course with a start and end date'
					] as item}
						<li class="flex gap-3 text-[0.95rem] leading-relaxed">
							<span class="mt-1 flex h-5 w-5 shrink-0 items-center justify-center rounded-full bg-white/5 text-xs text-muted">&#10007;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>
		</div>
	</div>
</section>

<!-- What You Get -->
<section class="relative py-20 md:py-32">
	<!-- Subtle background shift -->
	<div class="absolute inset-0 bg-gradient-to-b from-transparent via-surface/50 to-transparent"></div>

	<div class="relative mx-auto max-w-5xl px-6">
		<div class="reveal mx-auto max-w-3xl text-center">
			<span class="label-mono">What you get</span>
			<h2 class="mt-6 font-display text-3xl font-bold leading-tight text-heading md:text-5xl lg:text-6xl">
				A growing library.<br /><span class="text-gradient">A room full of people who use it.</span>
			</h2>
			<p class="mt-6 text-lg text-muted">Everything comes from real work. Not hypotheticals. Actual systems, templates, and workflows you can use today.</p>
		</div>

		<div class="mt-16 grid gap-4 md:grid-cols-2 lg:grid-cols-3">
			{#each features as feature, i}
				<div
					class="reveal card-elevated group rounded-2xl p-7"
					style="transition-delay: {i * 80}ms;"
				>
					<span class="font-mono text-[0.7rem] tracking-widest text-accent/60 uppercase">{feature.label}</span>
					<h3 class="mt-3 text-lg font-semibold text-heading">{feature.title}</h3>
					<p class="mt-3 text-sm leading-relaxed text-muted">{feature.desc}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Shimmer divider -->
<div class="shimmer-line"></div>

<!-- Who Is Ben -->
<section class="py-20 md:py-32">
	<div class="mx-auto max-w-4xl px-6">
		<div class="reveal mx-auto max-w-3xl text-center">
			<span class="label-mono">Built by</span>
			<h2 class="mt-6 font-display text-3xl font-bold leading-tight text-heading md:text-5xl lg:text-6xl">
				A dad, a worker, a builder.<br /><span class="text-gradient">In that order.</span>
			</h2>
		</div>

		<div class="mt-16 space-y-6">
			<div class="reveal rounded-2xl bg-surface p-8 md:p-12">
				<p class="text-lg leading-relaxed text-text md:text-xl">
					Ben is 37. Two young sons. Lives on Long Island. Works full-time at a tech startup. Runs a side consulting business doing AI automation for real companies. Builds products, tools, and experiments on nights and weekends.
				</p>
				<p class="mt-6 font-display text-2xl font-bold text-heading md:text-3xl">He uses AI for all of it.</p>
			</div>

			<div class="grid gap-4 md:grid-cols-2">
				{#each [
					{ label: 'For clients', text: 'Document intelligence pipelines for automotive financial data. AI-powered brand sites. Automation systems that save companies dozens of hours per week.' },
					{ label: 'For family', text: 'A bedtime story generator with mindfulness themes. An activity generator for parents who need ideas fast. A birthday coordination app that replaced 47 text threads.' },
					{ label: 'For the internet', text: 'BookmarkIQ (Chrome extension for Twitter bookmarks). Retell (AI video repurposing). A handful of open-source tools used by thousands.' },
					{ label: 'For fun', text: 'A hand-tracking particle system. An AI search engine using spatial metaphors. An AI operator named Cortana that runs 24/7 on a server and manages half his life.' }
				] as card, i}
					<div class="reveal card-elevated rounded-xl p-6" style="transition-delay: {i * 80}ms;">
						<span class="label-mono">{card.label}</span>
						<p class="mt-3 text-sm leading-relaxed text-muted">{card.text}</p>
					</div>
				{/each}
			</div>

			<p class="reveal text-center text-sm text-muted">
				The point is range. Not "AI for marketing" or "AI for developers." <span class="text-text">AI for everything.</span>
			</p>
		</div>
	</div>
</section>

<!-- Founding Members -->
<section id="founding" class="relative py-20 md:py-32">
	<div class="pointer-events-none absolute inset-0">
		<div class="animate-glow-pulse absolute top-1/2 left-1/2 h-[600px] w-[600px] -translate-x-1/2 -translate-y-1/2 rounded-full bg-accent/5 blur-[150px]"></div>
	</div>

	<div class="relative mx-auto max-w-3xl px-6 text-center">
		<div class="reveal">
			<span class="label-mono">Limited availability</span>
			<h2 class="mt-6 font-display text-3xl font-bold leading-tight text-heading md:text-5xl lg:text-6xl">
				50 founding spots.<br /><span class="text-gradient">$29/mo locked forever.</span>
			</h2>
			<p class="mt-6 text-lg text-muted">
				The first 50 members lock in $29/mo permanently. After that, the price goes to $49/mo.
			</p>
		</div>

		<!-- Pricing card -->
		<div class="reveal mx-auto mt-14 max-w-sm" style="transition-delay: 200ms;">
			<div class="overflow-hidden rounded-2xl border border-accent/15 bg-surface">
				<div class="border-b border-accent/10 px-8 py-8">
					<span class="label-mono">Founding Member</span>
					<div class="mt-4 flex items-baseline justify-center gap-1">
						<span class="font-display text-6xl font-extrabold text-heading">$29</span>
						<span class="text-lg text-muted">/mo</span>
					</div>
					<p class="mt-2 text-sm text-muted">Locked forever. Never increases.</p>
				</div>

				<div class="px-8 py-8">
					<ul class="space-y-3 text-left text-sm text-text">
						{#each [
							'Permanent price lock at $29/mo',
							'Free lifetime access on future platforms',
							'Founding member badge',
							'Permanent discounts on all future products',
							'Direct input on what gets built next'
						] as perk}
							<li class="flex gap-3">
								<span class="mt-0.5 flex h-5 w-5 shrink-0 items-center justify-center rounded-full bg-accent/10 text-xs text-accent">&#10003;</span>
								{perk}
							</li>
						{/each}
					</ul>

					<a
						href="#founding"
						class="group mt-8 flex w-full items-center justify-center rounded-lg bg-accent px-6 py-4 text-base font-semibold text-midnight transition-all duration-300 hover:bg-accent-light hover:shadow-xl hover:shadow-accent/20"
					>
						Lock in your spot
						<span class="ml-2 transition-transform duration-300 group-hover:translate-x-1">&rarr;</span>
					</a>
					<p class="mt-4 text-xs text-muted">Cancel anytime. No contracts.</p>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- FAQ -->
<section class="py-20 md:py-32">
	<div class="mx-auto max-w-2xl px-6">
		<div class="reveal text-center">
			<span class="label-mono">FAQ</span>
			<h2 class="mt-6 font-display text-3xl font-bold text-heading md:text-4xl">Questions</h2>
		</div>

		<div class="mt-12 space-y-2">
			{#each faqs as faq, i}
				<div class="reveal" style="transition-delay: {i * 60}ms;">
					<button
						onclick={() => toggleFaq(i)}
						class="w-full rounded-xl bg-surface px-6 py-5 text-left transition-all duration-300 hover:bg-surface-2"
					>
						<div class="flex items-center justify-between">
							<span class="text-[0.95rem] font-medium text-heading">{faq.q}</span>
							<span class="ml-4 flex h-6 w-6 shrink-0 items-center justify-center text-sm text-muted transition-all duration-300 {openFaq === i ? 'rotate-45 text-accent' : ''}">+</span>
						</div>
					</button>
					<div class="faq-content {openFaq === i ? 'open' : ''}">
						<div>
							<p class="px-6 pt-2 pb-5 text-sm leading-relaxed text-muted">{faq.a}</p>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Final CTA -->
<section class="relative py-20 md:py-32">
	<div class="shimmer-line"></div>
	<div class="relative mx-auto max-w-3xl px-6 pt-20 text-center">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-heading md:text-5xl lg:text-6xl">
				Real work. Real assets.<br /><span class="text-gradient">Real community.</span>
			</h2>
			<p class="mx-auto mt-6 max-w-lg text-lg text-muted">
				50 founding members. Full library access. Partner perks. Direct access. $29/mo locked forever.
			</p>
			<a
				href="#founding"
				class="group mt-10 inline-flex items-center rounded-lg bg-accent px-8 py-4 text-base font-semibold text-midnight transition-all duration-300 hover:bg-accent-light hover:shadow-xl hover:shadow-accent/20"
			>
				Become a founding member
				<span class="ml-2 transition-transform duration-300 group-hover:translate-x-1">&rarr;</span>
			</a>
		</div>
	</div>
</section>

<!-- Footer -->
<footer class="border-t border-border/50 py-10">
	<div class="mx-auto flex max-w-6xl flex-col items-center gap-4 px-6 text-sm text-muted md:flex-row md:justify-between">
		<span class="font-medium text-text/60">BuildsByBen &copy; {new Date().getFullYear()}</span>
		<div class="flex gap-6">
			<a href="https://x.com/xBenJamminx" target="_blank" rel="noopener" class="transition-colors duration-300 hover:text-accent">X / Twitter</a>
			<a href="https://buildsbyben.com" target="_blank" rel="noopener" class="transition-colors duration-300 hover:text-accent">Portfolio</a>
			<a href="https://github.com/xBenJamminx" target="_blank" rel="noopener" class="transition-colors duration-300 hover:text-accent">GitHub</a>
		</div>
	</div>
</footer>
