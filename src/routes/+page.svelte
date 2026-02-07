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

	const faqs = [
		{
			q: 'Is this a course?',
			a: "No. It's a living library. New resources added regularly from real work. No curriculum, no timeline. You get everything the moment you join, and it keeps growing."
		},
		{
			q: 'How is this different from free AI content on YouTube or Twitter?',
			a: 'Free content gives you the concept. This gives you the execution: actual prompts, exact configs, templates you can fork, and people to ask when you get stuck. Free content teaches the "what." This gives you the "how."'
		},
		{
			q: 'Do I need to be technical?',
			a: "No. Ben builds with AI, not with traditional coding expertise. If you can use Notion, Airtable, or a Chrome extension, you can use everything in here."
		},
		{
			q: "What if I'm not sure it's worth $29/mo?",
			a: "The template vault alone includes resources worth over $300 individually. The tool deals are designed to offset your membership cost entirely. Every resource added after you join is included at no extra cost. The library only gets more valuable over time."
		},
		{
			q: 'Can I cancel anytime?',
			a: 'Yes. Monthly billing. No contracts. Founding member pricing is locked as long as you stay subscribed. If you cancel and come back later, you rejoin at whatever the current price is.'
		},
		{
			q: "How much of Ben's time goes into this?",
			a: "Ben is in the community daily. Responds to questions, shares what he's building, drops resources in real time. Monthly AMAs and build sessions happen on a regular cadence. This isn't a content dump with no one behind it."
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

<!-- ============================================ -->
<!-- HERO -->
<!-- ============================================ -->
<section class="pt-28 pb-12 md:pt-40 md:pb-20">
	<div class="mx-auto max-w-5xl px-6">
		<div class="grid items-center gap-10 md:grid-cols-2">
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
					Stop watching tutorials and start shipping. Get the actual prompts, templates, repos, and workflows that a working dad uses to build real products every week.
				</p>

				<div class="{mounted ? 'reveal visible' : 'opacity-0'} mt-8 flex flex-wrap items-center gap-4">
					<a href="#founding" class="neo-btn rounded-xl bg-cyan px-7 py-3.5 text-base text-ink">
						Claim your founding spot &rarr;
					</a>
				</div>
				<span class="{mounted ? 'reveal visible' : 'opacity-0'} mt-3 inline-block font-mono text-sm text-muted">50 spots &middot; $29/mo locked forever &middot; Price goes to $49 after</span>
			</div>

			<!-- Visual anchor -->
			<div class="{mounted ? 'reveal visible' : 'opacity-0'} relative hidden md:block">
				<div class="relative mx-auto w-full max-w-sm">
					<div class="absolute top-6 left-6 right-0 h-64 rounded-2xl border-3 border-ink bg-yellow-light"></div>
					<div class="absolute top-3 left-3 right-3 h-64 rounded-2xl border-3 border-ink bg-pink-light"></div>
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
							<span class="font-mono text-xs text-muted">+12 new resources this week</span>
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

<!-- ============================================ -->
<!-- PROBLEM / SOLUTION (side by side) -->
<!-- ============================================ -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-5xl px-6">
		<div class="reveal">
			<div class="inline-block rounded-lg border-3 border-ink bg-pink-light px-4 py-1.5 font-mono text-xs font-bold uppercase tracking-wider text-ink shadow-[3px_3px_0_#000]">
				Sound familiar?
			</div>
			<h2 class="mt-6 font-display text-3xl font-bold leading-tight text-ink md:text-5xl">
				You're drowning in AI content. But nothing you can actually use.
			</h2>
		</div>

		<div class="mt-12 space-y-4">
			{#each [
				{
					problem: 'You watch a 20-minute YouTube tutorial',
					pain: 'Get inspired, then realize you have no idea how to actually implement it.',
					solution: 'Open a build guide with the exact prompts, configs, and steps. Follow along. Ship the thing.'
				},
				{
					problem: 'You save 47 AI Twitter threads',
					pain: 'Never open any of them again. They rot in your bookmarks.',
					solution: 'Open the prompt library. Find the one you need by category. Copy, paste, get results.'
				},
				{
					problem: 'You spend 3 hours researching which AI tool to use',
					pain: 'End up more confused than when you started. Still haven\'t picked one.',
					solution: 'Read the monthly honest roundup. Pick the right tool in 5 minutes. Move on.'
				},
				{
					problem: 'You get stuck and have nobody to ask',
					pain: 'Google it for an hour. Try 4 different things. Give up. Go back to doing it manually.',
					solution: 'Post in the community. Get an answer from someone who already solved it. Back on track in minutes.'
				},
				{
					problem: 'You see people shipping AI projects every week',
					pain: 'Wonder what you\'re missing. Feel further behind every day.',
					solution: 'Fork a template from the vault. Customize it. Ship your own thing this weekend.'
				}
			] as row, i}
				<div class="reveal grid gap-0 md:grid-cols-2" style="transition-delay: {i * 60}ms;">
					<!-- Problem side -->
					<div class="neo-card rounded-t-xl md:rounded-l-xl md:rounded-tr-none border-b-0 md:border-b-3 md:border-r-0 bg-surface p-6">
						<div class="mb-2 inline-block rounded-md border-2 border-ink/20 bg-pink-light px-2 py-0.5 font-mono text-[0.6rem] font-bold uppercase tracking-wider text-ink/60">Problem</div>
						<p class="font-semibold text-ink">{row.problem}</p>
						<p class="mt-1.5 text-sm text-muted">{row.pain}</p>
					</div>
					<!-- Solution side -->
					<div class="neo-card rounded-b-xl md:rounded-r-xl md:rounded-bl-none bg-cyan-bg p-6">
						<div class="mb-2 inline-block rounded-md border-2 border-ink bg-cyan px-2 py-0.5 font-mono text-[0.6rem] font-bold uppercase tracking-wider">Solution</div>
						<p class="text-sm font-medium leading-relaxed text-ink">{row.solution}</p>
					</div>
				</div>
			{/each}
		</div>

		<div class="reveal mt-10 rounded-2xl border-3 border-ink bg-yellow-bg p-8 text-center shadow-[6px_6px_0_theme(--color-yellow)]">
			<p class="font-display text-xl font-bold text-ink md:text-2xl">
				The gap isn't knowledge. It's execution.
			</p>
			<p class="mt-2 text-muted">
				You don't need another tutorial. You need the actual files, prompts, and systems someone is already using to get results.
			</p>
			<a href="#founding" class="neo-btn mt-6 inline-flex rounded-xl bg-cyan px-7 py-3 text-sm text-ink">
				Claim your founding spot &rarr;
			</a>
		</div>
	</div>
</section>

<!-- ============================================ -->
<!-- WHO THIS IS FOR (Audience Segments) -->
<!-- ============================================ -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-5xl px-6">
		<div class="reveal">
			<div class="inline-block rounded-lg border-3 border-ink bg-cyan-light px-4 py-1.5 font-mono text-xs font-bold uppercase tracking-wider text-ink shadow-[3px_3px_0_#000]">
				Who this is for
			</div>
			<h2 class="mt-6 font-display text-3xl font-bold leading-tight text-ink md:text-5xl">
				You're running a business, building on the side, and raising a family. AI should help with all three.
			</h2>
		</div>

		<div class="mt-12 grid gap-5 md:grid-cols-3">
			{#each [
				{
					who: 'Business Owners',
					badge: 'bg-cyan-light',
					shadow: 'neo-card-cyan',
					lines: [
						'You know AI can save you time and money but don\'t know where to start',
						'You\'re tired of hype and want practical, proven workflows',
						'You need systems you can implement this week, not next quarter'
					]
				},
				{
					who: 'Side Builders',
					badge: 'bg-yellow-light',
					shadow: 'neo-card-yellow',
					lines: [
						'You have a full-time job and a project you\'re building after hours',
						'You need to move fast with limited time and no team',
						'You want to see how someone else is actually shipping solo'
					]
				},
				{
					who: 'Parents Who Build',
					badge: 'bg-pink-light',
					shadow: 'neo-card-pink',
					lines: [
						'You\'re a business owner or side builder who also has kids',
						'You have 45 minutes after bedtime to make progress',
						'You need shortcuts that work on the first try so you can be present'
					]
				}
			] as segment, i}
				<div class="reveal neo-card {segment.shadow} rounded-2xl p-7" style="transition-delay: {i * 80}ms;">
					<span class="inline-block rounded-lg border-2 border-ink {segment.badge} px-3 py-1 font-mono text-xs font-bold uppercase tracking-wider">{segment.who}</span>
					<ul class="mt-5 space-y-3">
						{#each segment.lines as line}
							<li class="flex gap-2.5 text-sm leading-relaxed">
								<span class="mt-0.5 flex h-5 w-5 shrink-0 items-center justify-center rounded-md border-2 border-ink bg-surface text-xs font-bold">&#10003;</span>
								{line}
							</li>
						{/each}
					</ul>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- ============================================ -->
<!-- WHAT YOU GET (Tangible Outputs) -->
<!-- ============================================ -->
<section class="border-y-3 border-ink bg-bg-alt py-20 md:py-28">
	<div class="mx-auto max-w-5xl px-6">
		<div class="reveal">
			<div class="inline-block rounded-lg border-3 border-ink bg-yellow-light px-4 py-1.5 font-mono text-xs font-bold uppercase tracking-wider text-ink shadow-[3px_3px_0_#000]">
				What's inside
			</div>
			<h2 class="mt-6 font-display text-3xl font-bold text-ink md:text-5xl">
				Not theory. Not courses. Actual things you can use today.
			</h2>
		</div>

		<div class="mt-12 space-y-5">
			{#each [
				{
					num: '01',
					title: 'Build Guides and Breakdowns',
					desc: 'Step-by-step walkthroughs from real projects. Every guide includes the prompts, configs, and decisions so you can follow along or adapt to your own work.',
					examples: 'How I built a $0-to-launch GTM kit with AI. Turning 47 bookmarked threads into an organized system. Building a Chrome extension in a weekend.',
					badge: 'bg-cyan-light',
					shadow: 'neo-card-cyan'
				},
				{
					num: '02',
					title: 'Prompt Library',
					desc: 'Battle-tested prompts organized by use case: content creation, research, product planning, client work, and model optimization.',
					examples: 'Weekly content pipeline generator. Competitive analysis from a URL. Meeting notes to action items. Client proposal first draft.',
					badge: 'bg-yellow-light',
					shadow: 'neo-card-yellow'
				},
				{
					num: '03',
					title: 'Template Vault ($300+ value)',
					desc: 'Plug-and-play systems you can fork and start using in minutes. Each one is built from a real workflow, not a hypothetical.',
					examples: 'Content Pipeline. GTM Launch Kit (75+ directories). Product Spec Template. Competitive Analysis Framework. Client Onboarding System.',
					badge: 'bg-pink-light',
					shadow: 'neo-card-pink'
				},
				{
					num: '04',
					title: 'GitHub Repos You Can Fork and Ship',
					desc: 'Members-only repositories with functional code. Not toy demos. Starter kits, automation scripts, and boilerplates you can actually build on.',
					examples: 'Chrome extension starter. n8n workflow templates. API boilerplate. Content automation scripts.',
					badge: 'bg-cyan-light',
					shadow: 'neo-card-cyan'
				},
				{
					num: '05',
					title: 'Tool Deals and Honest Roundups',
					desc: 'Monthly "best AI tools" roundup with real assessments. Exclusive discounts negotiated with tool companies. Designed to save you more than the membership costs.',
					examples: 'Monthly tool roundup with pricing/verdict. Lifetime deal alerts. Model comparison when new releases drop.',
					badge: 'bg-yellow-light',
					shadow: 'neo-card-yellow'
				},
				{
					num: '06',
					title: 'Community, Livestreams, AMAs',
					desc: 'Topic channels for tools, building, wins, help, and off-topic. Ben is present daily. Monthly AMAs, build sessions, and office hours. All recordings archived.',
					examples: 'Live build sessions. Monthly AMA. Help channel with fast responses. Wins channel to share what you shipped.',
					badge: 'bg-pink-light',
					shadow: 'neo-card-pink'
				}
			] as feature, i}
				<div class="reveal neo-card {feature.shadow} rounded-2xl p-7 md:p-8" style="transition-delay: {i * 40}ms;">
					<div class="flex flex-col gap-4 md:flex-row md:items-start md:gap-6">
						<span class="inline-flex h-12 w-12 shrink-0 items-center justify-center rounded-xl border-3 border-ink {feature.badge} font-mono text-sm font-bold">{feature.num}</span>
						<div class="flex-1">
							<h3 class="font-display text-xl font-bold text-ink">{feature.title}</h3>
							<p class="mt-2 text-[0.95rem] leading-relaxed text-muted">{feature.desc}</p>
							<p class="mt-3 rounded-lg border-2 border-ink/10 bg-bg-alt px-4 py-3 font-mono text-xs leading-relaxed text-muted">
								<span class="font-bold text-ink">Examples:</span> {feature.examples}
							</p>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Mid-page CTA 2 -->
<div class="border-b-3 border-ink bg-cyan-bg py-10 text-center">
	<div class="reveal mx-auto max-w-2xl px-6">
		<p class="font-display text-xl font-bold text-ink md:text-2xl">Everything above. $29/mo. Cancel anytime.</p>
		<a href="#founding" class="neo-btn mt-5 inline-flex rounded-xl bg-yellow px-7 py-3 text-sm text-ink">
			Lock in founding pricing &rarr;
		</a>
	</div>
</div>

<!-- ============================================ -->
<!-- WHO IS BEN -->
<!-- ============================================ -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-4xl px-6">
		<div class="reveal">
			<div class="inline-block rounded-lg border-3 border-ink bg-green-light px-4 py-1.5 font-mono text-xs font-bold uppercase tracking-wider text-ink shadow-[3px_3px_0_#000]">
				Built by
			</div>
			<h2 class="mt-6 font-display text-3xl font-bold text-ink md:text-5xl">
				A dad, a worker, a builder. In that order.
			</h2>
		</div>

		<div class="reveal mt-10 rounded-2xl border-3 border-ink bg-surface p-8 shadow-[8px_8px_0_theme(--color-cyan)] md:p-12">
			<p class="text-lg leading-relaxed text-ink md:text-xl">
				Ben is 37. Two young sons. Long Island. Full-time at a tech startup Monday through Thursday. Side consulting business doing AI automation for real companies. Builds products on nights and weekends.
			</p>
			<p class="mt-6 font-display text-2xl font-bold text-ink md:text-3xl">He uses AI for all of it.</p>
			<p class="mt-4 text-muted leading-relaxed">
				Not as a hobby. Not as a thought experiment. As the core lever behind his work, his side business, his family life, and his creative projects. Every guide, template, and prompt in the community comes from something he actually built and shipped.
			</p>
		</div>

		<div class="mt-6 grid gap-5 md:grid-cols-4">
			{#each [
				{ label: 'Clients', text: 'Document intelligence pipelines. AI-powered brand sites. Automation saving companies dozens of hours/week.', color: 'bg-cyan-light', shadow: 'neo-card-cyan' },
				{ label: 'Family', text: 'Bedtime story generator. Activity engine. Birthday app that killed 47 text threads.', color: 'bg-yellow-light', shadow: 'neo-card-yellow' },
				{ label: 'Internet', text: 'BookmarkIQ. Retell. Open-source tools used by thousands of people.', color: 'bg-pink-light', shadow: 'neo-card-pink' },
				{ label: 'Fun', text: 'Particle systems. Spatial search. An AI operator named Cortana running 24/7.', color: 'bg-green-light', shadow: 'neo-card' }
			] as card, i}
				<div class="reveal neo-card {card.shadow} rounded-xl p-5" style="transition-delay: {i * 60}ms;">
					<span class="inline-block rounded-md border-2 border-ink {card.color} px-2.5 py-0.5 font-mono text-[0.65rem] font-bold uppercase tracking-wider">{card.label}</span>
					<p class="mt-3 text-sm leading-relaxed text-muted">{card.text}</p>
				</div>
			{/each}
		</div>

		<p class="reveal mt-8 text-center text-muted">
			Not "AI for marketing" or "AI for devs." <span class="font-semibold text-ink">AI for everything.</span> That range is what the community is built on.
		</p>
	</div>
</section>


<!-- ============================================ -->
<!-- FOUNDING MEMBERS -->
<!-- ============================================ -->
<section id="founding" class="border-b-3 border-ink bg-ink py-20 md:py-28">
	<div class="mx-auto max-w-4xl px-6">
		<div class="reveal text-center">
			<div class="mx-auto inline-block rounded-lg border-3 border-bg bg-yellow px-4 py-1.5 font-mono text-xs font-bold uppercase tracking-wider text-ink shadow-[3px_3px_0_theme(--color-cyan)]">
				Limited availability
			</div>
			<h2 class="mt-6 font-display text-3xl font-bold text-bg md:text-5xl">
				50 founding spots. $29/mo. Locked forever.
			</h2>
			<p class="mt-4 text-lg text-bg/60">
				The first 50 members lock in $29/mo permanently. After that, the price goes to $49/mo and never comes back down.
			</p>
		</div>

		<div class="mt-12 grid items-start gap-8 md:grid-cols-2">
			<!-- Pricing card -->
			<div class="reveal">
				<div class="rounded-2xl border-3 border-bg bg-surface shadow-[8px_8px_0_theme(--color-cyan)]">
					<div class="border-b-3 border-ink bg-cyan px-8 py-6 rounded-t-[13px]">
						<span class="font-mono text-sm font-bold uppercase tracking-widest text-ink">Founding Member</span>
						<div class="mt-3 flex items-baseline justify-center gap-1">
							<span class="font-display text-6xl font-extrabold text-ink">$29</span>
							<span class="text-xl text-ink/60">/mo</span>
						</div>
						<p class="mt-1 text-sm text-ink/60">Standard price: <span class="line-through">$49/mo</span></p>
					</div>

					<div class="px-8 py-8">
						<ul class="space-y-3 text-left text-sm">
							{#each [
								'Full library access (guides, prompts, templates, repos)',
								'Permanent price lock at $29/mo',
								'Free lifetime access on future platforms',
								'Founding member badge',
								'Discounts on all future paid products',
								'Direct input on what gets built next',
								'Early access to BookmarkIQ, Retell, and every future product'
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
							Claim your founding spot &rarr;
						</a>
						<p class="mt-4 text-center text-xs text-muted">Cancel anytime. No contracts.</p>
					</div>
				</div>
			</div>

			<!-- Why now -->
			<div class="reveal space-y-5" style="transition-delay: 100ms;">
				<div class="neo-card neo-card-cyan rounded-xl p-6">
					<h4 class="font-display text-lg font-bold text-ink">Price lock is permanent</h4>
					<p class="mt-2 text-sm text-muted">The $29/mo rate is locked as long as you stay subscribed. If you cancel and come back later, you pay whatever the current price is. There's no way to get the founding rate back.</p>
				</div>
				<div class="neo-card neo-card-yellow rounded-xl p-6">
					<h4 class="font-display text-lg font-bold text-ink">The library only gets bigger</h4>
					<p class="mt-2 text-sm text-muted">New guides, prompts, templates, and repos are added every week based on real work. The value compounds. Your price stays the same.</p>
				</div>
				<div class="neo-card neo-card-pink rounded-xl p-6">
					<h4 class="font-display text-lg font-bold text-ink">Tool deals offset the cost</h4>
					<p class="mt-2 text-sm text-muted">Exclusive discounts negotiated with AI tool companies. The goal is for the perks alone to save you more than $29/mo. The library and community are free upside.</p>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- ============================================ -->
<!-- FAQ -->
<!-- ============================================ -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-2xl px-6">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-ink md:text-4xl">Questions</h2>
		</div>

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

<!-- ============================================ -->
<!-- FINAL CTA -->
<!-- ============================================ -->
<section class="border-t-3 border-ink bg-cyan-bg py-20 md:py-28">
	<div class="mx-auto max-w-3xl px-6 text-center">
		<div class="reveal">
			<h2 class="font-display text-3xl font-bold text-ink md:text-5xl">
				Stop watching. Start shipping.
			</h2>
			<p class="mt-4 text-lg text-muted">
				50 founding spots. Full library access. Partner perks. Direct access to Ben. $29/mo locked forever.
			</p>
			<a
				href="#founding"
				class="neo-btn mt-10 inline-flex rounded-xl bg-cyan px-8 py-4 text-base text-ink"
			>
				Claim your founding spot &rarr;
			</a>
			<p class="mt-4 font-mono text-xs text-muted">Cancel anytime. No contracts. Price goes to $49/mo after 50 members.</p>
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
