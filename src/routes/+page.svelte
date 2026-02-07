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
			shadow: 'neo-card-cyan',
			badge: 'bg-cyan-light'
		},
		{
			title: 'Prompt Library',
			desc: 'Organized by use case. Each one tested and annotated with which model works best.',
			shadow: 'neo-card-yellow',
			badge: 'bg-yellow-light'
		},
		{
			title: 'Template Vault',
			desc: 'Fork and use in minutes. Content pipelines, GTM kits, competitive analysis frameworks.',
			shadow: 'neo-card-pink',
			badge: 'bg-pink-light'
		},
		{
			title: 'GitHub Repos',
			desc: 'Members-only code. Starter kits, automation scripts, boilerplates. Not toy demos.',
			shadow: 'neo-card-cyan',
			badge: 'bg-cyan-light'
		},
		{
			title: 'Tool Deals + Roundups',
			desc: 'Monthly honest assessments. Exclusive discounts designed to offset the membership cost.',
			shadow: 'neo-card-yellow',
			badge: 'bg-yellow-light'
		},
		{
			title: 'Chat, AMAs, Livestreams',
			desc: 'Daily founder presence. Monthly office hours. All recordings stay in the archive.',
			shadow: 'neo-card-pink',
			badge: 'bg-pink-light'
		}
	];

	const faqs = [
		{
			q: 'Is this a course?',
			a: "No. It's a living library. New resources added regularly from real work. No curriculum, no timeline. You get everything the moment you join."
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
			a: 'Yes. Monthly billing. No contracts. Founding pricing locked as long as you stay subscribed.'
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
<section class="pt-28 pb-12 md:pt-40 md:pb-20">
	<div class="mx-auto max-w-5xl px-6">
		<div class="grid items-center gap-10 md:grid-cols-2">
			<!-- Left: copy -->
			<div>
				<div class="{mounted ? 'reveal visible' : 'opacity-0'}">
					<div class="mb-6 inline-block rounded-lg border-3 border-ink bg-cyan px-4 py-1.5 font-mono text-xs font-medium uppercase tracking-wider text-ink shadow-[3px_3px_0_#000]">
						A living library for builders
					</div>
				</div>

				<h1 class="{mounted ? 'reveal visible' : 'opacity-0'} font-display text-5xl font-extrabold leading-[1.05] text-ink md:text-6xl lg:text-7xl">
					AI for your<br />whole life.
				</h1>

				<p class="{mounted ? 'reveal visible' : 'opacity-0'} mt-6 max-w-md text-lg leading-relaxed text-muted">
					Guides, prompts, templates, repos, and a community of people using AI for work, family, side projects, and the stuff in between.
				</p>

				<div class="{mounted ? 'reveal visible' : 'opacity-0'} mt-8 flex flex-wrap items-center gap-4">
					<a href="#founding" class="neo-btn rounded-xl bg-cyan px-7 py-3.5 text-base text-ink">
						Become a founding member &rarr;
					</a>
				</div>
				<span class="{mounted ? 'reveal visible' : 'opacity-0'} mt-3 inline-block font-mono text-sm text-muted">50 spots &middot; $29/mo locked forever</span>
			</div>

			<!-- Right: visual anchor - stacked preview cards -->
			<div class="{mounted ? 'reveal visible' : 'opacity-0'} relative hidden md:block">
				<div class="relative mx-auto w-full max-w-sm">
					<!-- Back card -->
					<div class="absolute top-6 left-6 right-0 h-64 rounded-2xl border-3 border-ink bg-yellow-light"></div>
					<!-- Middle card -->
					<div class="absolute top-3 left-3 right-3 h-64 rounded-2xl border-3 border-ink bg-pink-light"></div>
					<!-- Front card -->
					<div class="relative rounded-2xl border-3 border-ink bg-surface p-6 shadow-[6px_6px_0_#000]">
						<div class="flex items-center gap-3 border-b-2 border-ink/10 pb-4">
							<div class="flex h-10 w-10 items-center justify-center rounded-lg border-2 border-ink bg-cyan-light font-display text-lg font-bold">B</div>
							<div>
								<div class="font-display text-sm font-bold">BuildsByBen Library</div>
								<div class="font-mono text-xs text-muted">Updated today</div>
							</div>
						</div>
						<div class="mt-4 space-y-3">
							<div class="flex items-center gap-2">
								<div class="h-2.5 w-2.5 rounded-full border-2 border-ink bg-cyan"></div>
								<span class="text-sm font-medium">How I built a $0-to-launch GTM kit</span>
							</div>
							<div class="flex items-center gap-2">
								<div class="h-2.5 w-2.5 rounded-full border-2 border-ink bg-yellow"></div>
								<span class="text-sm font-medium">Prompt: weekly content pipeline</span>
							</div>
							<div class="flex items-center gap-2">
								<div class="h-2.5 w-2.5 rounded-full border-2 border-ink bg-pink"></div>
								<span class="text-sm font-medium">Template: competitive analysis</span>
							</div>
							<div class="flex items-center gap-2">
								<div class="h-2.5 w-2.5 rounded-full border-2 border-ink bg-green"></div>
								<span class="text-sm font-medium">Repo: Chrome extension starter</span>
							</div>
						</div>
						<div class="mt-4 flex items-center gap-2 rounded-lg border-2 border-ink/10 bg-bg-alt px-3 py-2">
							<span class="font-mono text-xs text-muted">+12 new this week</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Scrolling marquee -->
<div class="overflow-hidden border-y-3 border-ink bg-ink py-3.5">
	<div class="animate-marquee flex w-max gap-10 whitespace-nowrap">
		{#each Array(3) as _}
			<span class="font-display text-base font-bold text-bg">GUIDES FROM REAL PROJECTS</span>
			<span class="text-cyan">&bull;</span>
			<span class="font-display text-base font-bold text-bg">PROMPTS THAT ACTUALLY WORK</span>
			<span class="text-cyan">&bull;</span>
			<span class="font-display text-base font-bold text-bg">TEMPLATES YOU CAN FORK TODAY</span>
			<span class="text-cyan">&bull;</span>
			<span class="font-display text-base font-bold text-bg">CODE YOU CAN SHIP</span>
			<span class="text-cyan">&bull;</span>
			<span class="font-display text-base font-bold text-bg">A BUILDER WHO SHOWS UP DAILY</span>
			<span class="text-cyan">&bull;</span>
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

		<div class="mt-14 grid gap-6 lg:grid-cols-5">
			<!-- For you: takes 3 cols -->
			<div class="reveal neo-card rounded-2xl bg-cyan-bg p-8 lg:col-span-3">
				<div class="mb-5 inline-block rounded-lg border-2 border-ink bg-cyan px-3 py-1 font-mono text-xs font-bold uppercase tracking-wider">For you</div>
				<ul class="space-y-3.5">
					{#each [
						'A parent who wants to get more done so you can actually be present',
						'A full-time employee building something on the side',
						'A small business owner who knows AI can help but needs a starting point',
						'A freelancer, creator, or marketer who wants practical shortcuts'
					] as item}
						<li class="flex gap-3 text-[0.95rem] leading-relaxed">
							<span class="mt-0.5 flex h-6 w-6 shrink-0 items-center justify-center rounded-md border-2 border-ink bg-surface text-sm font-bold">&#10003;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>

			<!-- Not for you: takes 2 cols -->
			<div class="reveal neo-card rounded-2xl p-8 lg:col-span-2" style="transition-delay: 100ms;">
				<div class="mb-5 inline-block rounded-lg border-2 border-ink/30 bg-bg-alt px-3 py-1 font-mono text-xs font-bold uppercase tracking-wider text-muted">Not for you</div>
				<ul class="space-y-3.5 text-muted">
					{#each [
						'Looking for a get-rich-quick AI hustle',
						'A dev who reads model papers for fun',
						'Expecting a course with a start and end date'
					] as item}
						<li class="flex gap-3 text-[0.95rem] leading-relaxed">
							<span class="mt-0.5 flex h-6 w-6 shrink-0 items-center justify-center rounded-md border-2 border-ink/20 bg-surface text-sm text-ink/30">&#10007;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>
		</div>
	</div>
</section>

<!-- What You Get -->
<section class="border-y-3 border-ink bg-yellow-bg py-20 md:py-28">
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
					class="reveal neo-card {feature.shadow} rounded-xl p-6"
					style="transition-delay: {i * 60}ms;"
				>
					<div class="mb-4 inline-block rounded-lg border-2 border-ink {feature.badge} px-3 py-1 font-mono text-xs font-bold uppercase tracking-wider">
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
				A dad, a worker, a builder.<br />In that order.
			</h2>
		</div>

		<div class="reveal mt-10 rounded-2xl border-3 border-ink bg-surface p-8 shadow-[8px_8px_0_theme(--color-cyan)] md:p-12">
			<p class="text-lg leading-relaxed text-ink md:text-xl">
				Ben is 37. Two young sons. Long Island. Full-time at a tech startup. Side consulting business doing AI automation for real companies. Builds products on nights and weekends.
			</p>
			<p class="mt-6 font-display text-2xl font-bold text-ink md:text-3xl">He uses AI for all of it.</p>
		</div>

		<div class="mt-6 grid gap-5 md:grid-cols-4">
			{#each [
				{ label: 'Clients', text: 'Document intelligence. AI-powered sites. Automation saving dozens of hours/week.', color: 'bg-cyan-light', shadow: 'neo-card-cyan' },
				{ label: 'Family', text: 'Bedtime story generator. Activity engine. Birthday app that killed 47 text threads.', color: 'bg-yellow-light', shadow: 'neo-card-yellow' },
				{ label: 'Internet', text: 'BookmarkIQ. Retell. Open-source tools used by thousands.', color: 'bg-pink-light', shadow: 'neo-card-pink' },
				{ label: 'Fun', text: 'Particle systems. Spatial search. An AI operator named Cortana running 24/7.', color: 'bg-green-light', shadow: 'neo-card' }
			] as card, i}
				<div class="reveal neo-card {card.shadow} rounded-xl p-5" style="transition-delay: {i * 60}ms;">
					<span class="inline-block rounded-md border-2 border-ink {card.color} px-2.5 py-0.5 font-mono text-[0.65rem] font-bold uppercase tracking-wider">{card.label}</span>
					<p class="mt-3 text-sm leading-relaxed text-muted">{card.text}</p>
				</div>
			{/each}
		</div>

		<p class="reveal mt-8 text-center text-muted">
			Not "AI for marketing" or "AI for devs." <span class="font-semibold text-ink">AI for everything.</span> That's what the community is built on.
		</p>
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
			<div class="rounded-2xl border-3 border-bg bg-surface shadow-[8px_8px_0_theme(--color-cyan)]">
				<div class="border-b-3 border-ink bg-cyan px-8 py-6 rounded-t-[13px]">
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
<section class="border-t-3 border-ink bg-cyan-bg py-20 md:py-28">
	<div class="mx-auto max-w-3xl px-6 text-center">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-ink md:text-5xl">
				Real work. Real assets.<br />Real community.
			</h2>
			<p class="mt-4 text-lg text-muted">
				50 founding spots. Full library. Partner perks. Direct access. $29/mo locked forever.
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
