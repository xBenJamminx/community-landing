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
			{ threshold: 0.1, rootMargin: '0px 0px -60px 0px' }
		);

		document.querySelectorAll('.reveal').forEach((el) => observer.observe(el));

		return () => observer.disconnect();
	});

	const features = [
		{
			title: 'Guides and Breakdowns',
			desc: 'Written from real projects, not theory. How-tos, build breakdowns, experiment reports, tool deep dives, and workflow walkthroughs. Every guide includes the prompts, configs, and steps to actually do the thing yourself.',
			icon: 'G'
		},
		{
			title: 'Prompt Library',
			desc: 'Organized by category: content creation, research, product planning, client work, personal use, and model optimization. Each prompt includes context on when to use it and which model works best.',
			icon: 'P'
		},
		{
			title: 'Template Vault',
			desc: 'Plug-and-play systems you can fork and start using in minutes. Content Pipeline, GTM Launch Kit (75+ directories), Product Spec Template, Competitive Analysis Framework, and more added regularly.',
			icon: 'T'
		},
		{
			title: 'GitHub Repos',
			desc: 'Members-only repositories you can fork and run. Starter kits, automation scripts, boilerplates, and example projects. Not toy demos. Functional code you can build on.',
			icon: 'R'
		},
		{
			title: 'Roundups and Curation',
			desc: 'Monthly "best AI tools" roundup with honest assessments. Model comparison breakdowns when new releases drop. Deal alerts for lifetime deals, free trials, and discounts.',
			icon: 'C'
		},
		{
			title: 'Tool Deals and Partner Perks',
			desc: 'Exclusive discounts negotiated with AI tool companies. The goal is to save you more than the membership costs. Active deals listed on a dedicated perks page.',
			icon: 'D'
		},
		{
			title: 'Community Chat',
			desc: 'Topic channels for tools, building, wins, help, off-topic, and parents. Ben is present daily. The vibe is a group chat with a smart friend, not a corporate Slack.',
			icon: 'H'
		},
		{
			title: 'Livestreams and Calls',
			desc: 'Build sessions when something interesting is happening. Monthly AMA and office hours. All recordings stay in the community for members who miss it live.',
			icon: 'L'
		},
		{
			title: 'Early Access to Products',
			desc: 'First to try BookmarkIQ, Retell, and every future product before public launch. Vote on features, give feedback, and shape what gets built next.',
			icon: 'E'
		}
	];

	const faqs = [
		{
			q: 'Is this a course?',
			a: "No. It's a living library and community. New guides, prompts, templates, and repos are added regularly based on real work. There's no curriculum, no start date, no end date. You get access to everything the moment you join, and the library keeps growing."
		},
		{
			q: 'How is this different from free AI content on YouTube or Twitter?',
			a: 'Free content gives you the concept. The community gives you the execution. The actual prompts, the exact configs, the step-by-step walkthroughs, the templates you can fork, and the support to get unstuck. Free content teaches the "what." The community gives you the "how."'
		},
		{
			q: 'Do I need to be technical?',
			a: "No. Ben builds with AI, not with traditional coding expertise. Most guides are written for people who are comfortable using apps and tools but aren't developers. If you can use Notion, Airtable, or a Chrome extension, you can use what's in here."
		},
		{
			q: "How much of Ben's time goes into this?",
			a: "Ben is in the community daily. He responds to questions, shares what he's working on, and drops resources as he builds them. Monthly AMAs and livestreams happen on a regular cadence. This isn't a content dump with no presence behind it."
		},
		{
			q: 'Can I cancel anytime?',
			a: 'Yes. Monthly billing, cancel whenever you want. No contracts, no commitments. Founding member pricing is locked as long as you stay subscribed. If you cancel and come back, you rejoin at the current price.'
		},
		{
			q: "What if I'm not sure it's worth $29/mo?",
			a: 'The template vault alone includes over $300 worth of resources sold individually. The tool deals and partner perks are designed to offset the membership cost entirely. Every guide, prompt, and repo added after you join is included at no extra charge. The library only gets more valuable over time.'
		}
	];

	const foundingPerks = [
		'Permanent price lock at $29/mo for as long as you stay',
		'Free lifetime access when the community migrates to a larger platform',
		'Founding member badge in the community',
		'Permanent discounts on all future paid products',
		'Direct input on what gets built and prioritized next'
	];
</script>

<svelte:head>
	<title>BuildsByBen Community - AI for your whole life</title>
</svelte:head>

<!-- Nav -->
<nav class="fixed top-0 z-50 w-full border-b border-border/50 bg-midnight/80 backdrop-blur-xl">
	<div class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4">
		<span class="text-lg font-bold tracking-tight text-heading">Builds<span class="text-gradient">ByBen</span></span>
		<a
			href="#founding"
			class="rounded-lg bg-accent px-5 py-2.5 text-sm font-semibold text-midnight transition-all duration-300 hover:bg-accent-light hover:shadow-lg hover:shadow-accent/20"
		>
			Join the Community
		</a>
	</div>
</nav>

<!-- Hero -->
<section class="relative overflow-hidden pt-32 pb-24 md:pt-48 md:pb-36">
	<!-- Animated background orbs -->
	<div class="pointer-events-none absolute inset-0">
		<div class="animate-glow-pulse absolute top-20 left-1/4 h-96 w-96 rounded-full bg-accent/10 blur-3xl"></div>
		<div class="animate-glow-pulse absolute right-1/4 bottom-20 h-72 w-72 rounded-full bg-warm/10 blur-3xl delay-200" style="animation-delay: 2s;"></div>
	</div>
	<div class="relative mx-auto max-w-4xl px-6 text-center">
		<h1 class="{mounted ? 'animate-fade-up' : 'opacity-0'} text-4xl font-extrabold leading-tight tracking-tight text-heading md:text-6xl lg:text-7xl">
			AI for your whole life.<br />
			<span class="text-gradient">Not just your job.</span>
		</h1>
		<p class="{mounted ? 'animate-fade-up delay-200' : 'opacity-0'} mx-auto mt-6 max-w-2xl text-lg leading-relaxed text-muted md:text-xl">
			Guides, prompts, templates, repos, and a community of people using AI for work, family, side projects, and the random stuff in between. Built by a dad who does all four every single day.
		</p>
		<div class="{mounted ? 'animate-fade-up delay-400' : 'opacity-0'} mt-10 flex flex-col items-center gap-3">
			<a
				href="#founding"
				class="group relative inline-flex items-center overflow-hidden rounded-xl bg-accent px-8 py-4 text-lg font-bold text-midnight shadow-lg shadow-accent/20 transition-all duration-300 hover:bg-accent-light hover:shadow-xl hover:shadow-accent/30"
			>
				<span class="relative z-10">Join as a Founding Member</span>
				<span class="relative z-10 ml-2 transition-transform duration-300 group-hover:translate-x-1">&rarr;</span>
			</a>
			<p class="text-sm text-muted">First 50 members only. Standard price is $49/mo.</p>
		</div>
	</div>
</section>

<!-- Social Proof Bar -->
<section class="border-y border-border/50 bg-deep py-8">
	<div class="mx-auto flex max-w-5xl flex-wrap items-center justify-center gap-x-12 gap-y-4 px-6 text-center text-sm text-muted">
		<div class="reveal"><span class="text-xl font-bold text-accent-light">$300+</span> <span class="ml-1">in templates included free</span></div>
		<div class="hidden h-6 w-px bg-border/50 md:block"></div>
		<div class="reveal" style="transition-delay: 100ms;"><span class="text-xl font-bold text-accent-light">75+</span> <span class="ml-1">launch directories mapped</span></div>
		<div class="hidden h-6 w-px bg-border/50 md:block"></div>
		<div class="reveal" style="transition-delay: 200ms;"><span class="text-xl font-bold text-accent-light">9</span> <span class="ml-1">categories of member resources</span></div>
		<div class="hidden h-6 w-px bg-border/50 md:block"></div>
		<div class="reveal" style="transition-delay: 300ms;"><span class="text-xl font-bold text-accent-light">Daily</span> <span class="ml-1">founder presence</span></div>
	</div>
</section>

<!-- Who This Is For -->
<section class="py-24 md:py-32">
	<div class="mx-auto max-w-4xl px-6">
		<div class="reveal">
			<h2 class="text-center text-3xl font-bold text-heading md:text-5xl">
				You know AI matters.<br /><span class="text-gradient">You just don't have 6 hours to figure it out.</span>
			</h2>
			<p class="mx-auto mt-6 max-w-2xl text-center text-lg leading-relaxed text-muted">
				This is for the person with a full-time job, a family, maybe a side project, and about 45 minutes of free time after the kids go to bed.
			</p>
		</div>
		<div class="mt-14 grid gap-8 md:grid-cols-2">
			<div class="reveal card-hover rounded-2xl border border-border/50 bg-surface p-8">
				<h3 class="mb-5 text-lg font-semibold text-heading">This is for you if you are:</h3>
				<ul class="space-y-3.5 text-text">
					{#each [
						'A parent who wants to get more done in less time so you can actually be present',
						'A full-time employee building something on the side',
						'A small business owner who knows AI can help but doesn\'t know where to start',
						'A freelancer, creator, or marketer who wants practical shortcuts',
						'Someone who wants to use AI beyond basic chatbot conversations'
					] as item}
						<li class="flex gap-3">
							<span class="mt-0.5 flex h-5 w-5 shrink-0 items-center justify-center rounded-full bg-accent/15 text-xs text-accent-light">&#10003;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>
			<div class="reveal card-hover rounded-2xl border border-border/50 bg-surface p-8" style="transition-delay: 150ms;">
				<h3 class="mb-5 text-lg font-semibold text-heading">This is not for you if you are:</h3>
				<ul class="space-y-3.5 text-muted">
					{#each [
						'Looking for a get-rich-quick AI hustle community',
						'A developer who already lives in VS Code and reads model papers for fun',
						'Expecting a course with a start and end date'
					] as item}
						<li class="flex gap-3">
							<span class="mt-0.5 flex h-5 w-5 shrink-0 items-center justify-center rounded-full bg-red-500/10 text-xs text-red-400">&#10007;</span>
							{item}
						</li>
					{/each}
				</ul>
			</div>
		</div>
	</div>
</section>

<!-- What You Get -->
<section class="border-t border-border/50 bg-deep py-24 md:py-32">
	<div class="mx-auto max-w-6xl px-6">
		<div class="reveal text-center">
			<h2 class="text-3xl font-bold text-heading md:text-5xl">
				A growing library. <span class="text-gradient">A room full of people who use it.</span>
			</h2>
			<p class="mx-auto mt-4 max-w-xl text-muted">
				Everything comes from real work. Not hypotheticals. Not listicles. Actual systems, templates, and workflows you can use today.
			</p>
		</div>
		<div class="mt-14 grid gap-5 sm:grid-cols-2 lg:grid-cols-3">
			{#each features as feature, i}
				<div
					class="reveal card-hover group rounded-2xl border border-border/50 bg-surface p-6"
					style="transition-delay: {i * 80}ms;"
				>
					<div class="mb-4 inline-flex h-11 w-11 items-center justify-center rounded-xl bg-gradient-to-br from-accent/20 to-warm/10 text-base font-bold text-accent-light transition-transform duration-300 group-hover:scale-110">
						{feature.icon}
					</div>
					<h3 class="mb-2 text-lg font-semibold text-heading">{feature.title}</h3>
					<p class="text-sm leading-relaxed text-muted">{feature.desc}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Who Is Ben -->
<section class="py-24 md:py-32">
	<div class="mx-auto max-w-4xl px-6">
		<div class="reveal">
			<h2 class="text-center text-3xl font-bold text-heading md:text-5xl">
				A dad, a full-time worker, and a builder.<br /><span class="text-gradient">In that order.</span>
			</h2>
		</div>
		<div class="mt-12 space-y-8 text-lg leading-relaxed text-text">
			<p class="reveal">
				Ben is 37. Two young sons. Lives on Long Island. Works full-time at a tech startup. Runs a side consulting business doing AI automation for real companies. Builds products, tools, and experiments on nights and weekends.
			</p>
			<p class="reveal text-xl font-medium text-heading">He uses AI for all of it.</p>
			<div class="grid gap-5 md:grid-cols-2">
				<div class="reveal card-hover rounded-xl border border-border/50 bg-surface p-6">
					<h4 class="mb-3 text-xs font-bold tracking-widest text-accent-light uppercase">For clients</h4>
					<p class="text-sm leading-relaxed text-muted">Document intelligence pipelines for automotive financial data. AI-powered brand sites. Automation systems that save companies dozens of hours per week.</p>
				</div>
				<div class="reveal card-hover rounded-xl border border-border/50 bg-surface p-6" style="transition-delay: 100ms;">
					<h4 class="mb-3 text-xs font-bold tracking-widest text-accent-light uppercase">For family</h4>
					<p class="text-sm leading-relaxed text-muted">A bedtime story generator with mindfulness themes. An activity generator for parents who need ideas fast. A birthday coordination app that replaced 47 text threads.</p>
				</div>
				<div class="reveal card-hover rounded-xl border border-border/50 bg-surface p-6" style="transition-delay: 200ms;">
					<h4 class="mb-3 text-xs font-bold tracking-widest text-accent-light uppercase">For the internet</h4>
					<p class="text-sm leading-relaxed text-muted">BookmarkIQ (Chrome extension for Twitter bookmarks). Retell (AI video repurposing). A handful of open-source tools used by thousands.</p>
				</div>
				<div class="reveal card-hover rounded-xl border border-border/50 bg-surface p-6" style="transition-delay: 300ms;">
					<h4 class="mb-3 text-xs font-bold tracking-widest text-accent-light uppercase">For fun</h4>
					<p class="text-sm leading-relaxed text-muted">A hand-tracking particle system. An AI search engine using spatial metaphors. An AI operator named Cortana that runs 24/7 on a server and manages half his life.</p>
				</div>
			</div>
			<p class="reveal text-center text-muted">
				The point is range. Not "AI for marketing" or "AI for developers." AI for everything. That range is what the community is built on.
			</p>
		</div>
	</div>
</section>

<!-- Founding Members -->
<section id="founding" class="relative border-t border-border/50 bg-deep py-24 md:py-32">
	<div class="pointer-events-none absolute inset-0">
		<div class="animate-glow-pulse absolute right-1/3 bottom-0 h-96 w-96 rounded-full bg-accent/8 blur-3xl"></div>
	</div>
	<div class="relative mx-auto max-w-3xl px-6 text-center">
		<div class="reveal">
			<h2 class="text-3xl font-bold text-heading md:text-5xl">
				50 founding spots.<br /><span class="text-gradient">$29/mo locked forever.</span>
			</h2>
			<p class="mx-auto mt-6 max-w-xl text-lg text-muted">
				The first 50 members pay $29/mo. That price never changes for them, regardless of what happens next. After 50 founding members, the price goes to $49/mo.
			</p>
		</div>
		<div class="reveal mx-auto mt-10 max-w-md overflow-hidden rounded-2xl border border-accent/20 bg-surface shadow-2xl shadow-accent/5" style="transition-delay: 200ms;">
			<div class="bg-gradient-to-r from-accent/10 to-warm/10 px-8 py-6">
				<span class="text-sm font-semibold tracking-widest text-accent-light uppercase">Founding Member</span>
				<div class="mt-3 flex items-baseline justify-center gap-1">
					<span class="text-6xl font-extrabold text-heading">$29</span>
					<span class="text-xl text-muted">/mo</span>
				</div>
				<p class="mt-1 text-sm text-muted">Locked forever. Never increases.</p>
			</div>
			<div class="px-8 py-8">
				<ul class="mb-8 space-y-3.5 text-left text-sm text-text">
					{#each foundingPerks as perk}
						<li class="flex gap-3">
							<span class="mt-0.5 flex h-5 w-5 shrink-0 items-center justify-center rounded-full bg-accent/15 text-xs text-accent-light">&#10003;</span>
							{perk}
						</li>
					{/each}
				</ul>
				<a
					href="#founding"
					class="group block w-full rounded-xl bg-gradient-to-r from-accent to-warm px-6 py-4 text-center text-lg font-bold text-midnight shadow-lg shadow-accent/20 transition-all duration-300 hover:shadow-xl hover:shadow-accent/30 hover:brightness-110"
				>
					Lock in your founding spot
					<span class="ml-1 inline-block transition-transform duration-300 group-hover:translate-x-1">&rarr;</span>
				</a>
				<p class="mt-4 text-xs text-muted">Cancel anytime. No contracts.</p>
			</div>
		</div>
		<p class="reveal mt-10 text-sm text-muted" style="transition-delay: 400ms;">
			The library grows every week. The value compounds. The price only goes up.
		</p>
	</div>
</section>

<!-- FAQ -->
<section class="py-24 md:py-32">
	<div class="mx-auto max-w-3xl px-6">
		<h2 class="reveal mb-12 text-center text-3xl font-bold text-heading md:text-4xl">
			Questions
		</h2>
		<div class="space-y-3">
			{#each faqs as faq, i}
				<div class="reveal" style="transition-delay: {i * 60}ms;">
					<button
						onclick={() => toggleFaq(i)}
						class="w-full rounded-xl border border-border/50 bg-surface px-6 py-5 text-left transition-all duration-300 hover:border-accent/20 hover:bg-surface/80"
					>
						<div class="flex items-center justify-between">
							<span class="font-semibold text-heading">{faq.q}</span>
							<span class="ml-4 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-border/50 text-sm text-muted transition-all duration-300 {openFaq === i ? 'rotate-45 bg-accent/20 text-accent-light' : ''}">+</span>
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
<section class="relative border-t border-border/50 bg-deep py-24 md:py-32">
	<div class="pointer-events-none absolute inset-0">
		<div class="animate-glow-pulse absolute top-1/2 left-1/2 h-96 w-96 -translate-x-1/2 -translate-y-1/2 rounded-full bg-accent/8 blur-3xl"></div>
	</div>
	<div class="relative mx-auto max-w-3xl px-6 text-center">
		<div class="reveal">
			<h2 class="text-3xl font-bold text-heading md:text-5xl">
				Real work. Real assets.<br /><span class="text-gradient">Real community.</span>
			</h2>
			<p class="mx-auto mt-4 max-w-xl text-lg text-muted">
				Join 50 founding members getting the full library, partner perks, and direct access for $29/mo. That price is gone once the spots fill.
			</p>
			<a
				href="#founding"
				class="group mt-8 inline-flex items-center rounded-xl bg-gradient-to-r from-accent to-warm px-8 py-4 text-lg font-bold text-midnight shadow-lg shadow-accent/20 transition-all duration-300 hover:shadow-xl hover:shadow-accent/30 hover:brightness-110"
			>
				Become a Founding Member
				<span class="ml-2 transition-transform duration-300 group-hover:translate-x-1">&rarr;</span>
			</a>
		</div>
	</div>
</section>

<!-- Footer -->
<footer class="border-t border-border/50 py-10">
	<div class="mx-auto flex max-w-6xl flex-col items-center gap-4 px-6 text-sm text-muted md:flex-row md:justify-between">
		<span class="font-medium">Builds<span class="text-gradient">ByBen</span> &copy; {new Date().getFullYear()}</span>
		<div class="flex gap-6">
			<a href="https://x.com/xBenJamminx" target="_blank" rel="noopener" class="transition-colors duration-300 hover:text-accent-light">X / Twitter</a>
			<a href="https://buildsbyben.com" target="_blank" rel="noopener" class="transition-colors duration-300 hover:text-accent-light">Portfolio</a>
			<a href="https://github.com/xBenJamminx" target="_blank" rel="noopener" class="transition-colors duration-300 hover:text-accent-light">GitHub</a>
		</div>
	</div>
</footer>
