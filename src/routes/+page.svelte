<script lang="ts">
	let openFaq = $state<number | null>(null);

	function toggleFaq(index: number) {
		openFaq = openFaq === index ? null : index;
	}

	const features = [
		{
			title: 'Guides and Breakdowns',
			desc: 'Written from real projects, not theory. How-tos, build breakdowns, experiment reports, tool deep dives, and workflow walkthroughs. Every guide includes the prompts, configs, and steps to actually do the thing yourself.',
			icon: '01'
		},
		{
			title: 'Prompt Library',
			desc: 'Organized by category: content creation, research, product planning, client work, personal use, and model optimization. Each prompt includes context on when to use it and which model works best.',
			icon: '02'
		},
		{
			title: 'Template Vault',
			desc: 'Plug-and-play systems you can fork and start using in minutes. Content Pipeline, GTM Launch Kit (75+ directories), Product Spec Template, Competitive Analysis Framework, and more added regularly.',
			icon: '03'
		},
		{
			title: 'GitHub Repos',
			desc: 'Members-only repositories you can fork and run. Starter kits, automation scripts, boilerplates, and example projects. Not toy demos. Functional code you can build on.',
			icon: '04'
		},
		{
			title: 'Roundups and Curation',
			desc: 'Monthly "best AI tools" roundup with honest assessments. Model comparison breakdowns when new releases drop. Deal alerts for lifetime deals, free trials, and discounts.',
			icon: '05'
		},
		{
			title: 'Tool Deals and Partner Perks',
			desc: 'Exclusive discounts negotiated with AI tool companies. The goal is to save you more than the membership costs. Active deals listed on a dedicated perks page.',
			icon: '06'
		},
		{
			title: 'Community Chat',
			desc: 'Topic channels for tools, building, wins, help, off-topic, and parents. Ben is present daily. The vibe is a group chat with a smart friend, not a corporate Slack.',
			icon: '07'
		},
		{
			title: 'Livestreams and Calls',
			desc: 'Build sessions when something interesting is happening. Monthly AMA and office hours. All recordings stay in the community for members who miss it live.',
			icon: '08'
		},
		{
			title: 'Early Access to Products',
			desc: 'First to try BookmarkIQ, Retell, and every future product before public launch. Vote on features, give feedback, and shape what gets built next.',
			icon: '09'
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
		<span class="text-lg font-bold text-heading">BuildsByBen</span>
		<a
			href="#founding"
			class="rounded-lg bg-accent px-5 py-2.5 text-sm font-semibold text-white transition hover:bg-accent-glow"
		>
			Join the Community
		</a>
	</div>
</nav>

<!-- Hero -->
<section class="relative overflow-hidden pt-32 pb-20 md:pt-44 md:pb-32">
	<div class="pointer-events-none absolute inset-0 bg-[radial-gradient(ellipse_at_top,_var(--color-accent-glow)_0%,_transparent_50%)] opacity-15"></div>
	<div class="relative mx-auto max-w-4xl px-6 text-center">
		<h1 class="text-4xl font-extrabold leading-tight tracking-tight text-heading md:text-6xl lg:text-7xl">
			AI for your whole life.<br />
			<span class="text-accent-light">Not just your job.</span>
		</h1>
		<p class="mx-auto mt-6 max-w-2xl text-lg leading-relaxed text-muted md:text-xl">
			Guides, prompts, templates, repos, and a community of people using AI for work, family, side projects, and the random stuff in between. Built by a dad who does all four every single day.
		</p>
		<div class="mt-10 flex flex-col items-center gap-3">
			<a
				href="#founding"
				class="inline-flex items-center rounded-xl bg-accent px-8 py-4 text-lg font-bold text-white shadow-lg shadow-accent-glow/25 transition hover:bg-accent-glow hover:shadow-accent-glow/40"
			>
				Join as a Founding Member &mdash; $29/mo
			</a>
			<p class="text-sm text-muted">First 50 members only. Standard price is $49/mo.</p>
		</div>
	</div>
</section>

<!-- Social Proof Bar -->
<section class="border-y border-border/50 bg-deep py-8">
	<div class="mx-auto flex max-w-5xl flex-wrap items-center justify-center gap-x-12 gap-y-4 px-6 text-center text-sm text-muted">
		<div><span class="font-bold text-heading">$300+</span> in templates included free</div>
		<div class="hidden h-4 w-px bg-border md:block"></div>
		<div><span class="font-bold text-heading">75+</span> launch directories mapped</div>
		<div class="hidden h-4 w-px bg-border md:block"></div>
		<div><span class="font-bold text-heading">9</span> categories of member resources</div>
		<div class="hidden h-4 w-px bg-border md:block"></div>
		<div><span class="font-bold text-heading">Daily</span> founder presence</div>
	</div>
</section>

<!-- Who This Is For -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-4xl px-6">
		<h2 class="text-center text-3xl font-bold text-heading md:text-4xl">
			You know AI matters.<br />You just don't have 6 hours to figure it out.
		</h2>
		<p class="mx-auto mt-6 max-w-2xl text-center text-lg leading-relaxed text-muted">
			This is for the person with a full-time job, a family, maybe a side project, and about 45 minutes of free time after the kids go to bed.
		</p>
		<div class="mt-14 grid gap-8 md:grid-cols-2">
			<div class="rounded-2xl border border-border/50 bg-surface p-8">
				<h3 class="mb-5 text-lg font-semibold text-heading">This is for you if you are:</h3>
				<ul class="space-y-3 text-text">
					<li class="flex gap-3">
						<span class="mt-0.5 text-accent-light">&#10003;</span>
						A parent who wants to get more done in less time so you can actually be present
					</li>
					<li class="flex gap-3">
						<span class="mt-0.5 text-accent-light">&#10003;</span>
						A full-time employee building something on the side
					</li>
					<li class="flex gap-3">
						<span class="mt-0.5 text-accent-light">&#10003;</span>
						A small business owner who knows AI can help but doesn't know where to start
					</li>
					<li class="flex gap-3">
						<span class="mt-0.5 text-accent-light">&#10003;</span>
						A freelancer, creator, or marketer who wants practical shortcuts
					</li>
					<li class="flex gap-3">
						<span class="mt-0.5 text-accent-light">&#10003;</span>
						Someone who wants to use AI beyond basic chatbot conversations
					</li>
				</ul>
			</div>
			<div class="rounded-2xl border border-border/50 bg-surface p-8">
				<h3 class="mb-5 text-lg font-semibold text-heading">This is not for you if you are:</h3>
				<ul class="space-y-3 text-muted">
					<li class="flex gap-3">
						<span class="mt-0.5 text-red-400">&#10007;</span>
						Looking for a get-rich-quick AI hustle community
					</li>
					<li class="flex gap-3">
						<span class="mt-0.5 text-red-400">&#10007;</span>
						A developer who already lives in VS Code and reads model papers for fun
					</li>
					<li class="flex gap-3">
						<span class="mt-0.5 text-red-400">&#10007;</span>
						Expecting a course with a start and end date
					</li>
				</ul>
			</div>
		</div>
	</div>
</section>

<!-- What You Get -->
<section class="border-t border-border/50 bg-deep py-20 md:py-28">
	<div class="mx-auto max-w-6xl px-6">
		<div class="text-center">
			<h2 class="text-3xl font-bold text-heading md:text-4xl">
				A growing library of real assets.<br />A room full of people who use them.
			</h2>
			<p class="mx-auto mt-4 max-w-xl text-muted">
				Everything in the library comes from real work. Not hypotheticals. Not listicles. Actual systems, templates, and workflows you can use today.
			</p>
		</div>
		<div class="mt-14 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
			{#each features as feature}
				<div class="group rounded-2xl border border-border/50 bg-surface p-6 transition hover:border-accent/30 hover:bg-surface/80">
					<div class="mb-4 inline-flex h-10 w-10 items-center justify-center rounded-lg bg-accent/10 text-sm font-bold text-accent-light">
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
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-4xl px-6">
		<h2 class="text-center text-3xl font-bold text-heading md:text-4xl">
			A dad, a full-time worker, and a builder. In that order.
		</h2>
		<div class="mt-12 space-y-8 text-lg leading-relaxed text-text">
			<p>
				Ben is 37. Two young sons. Lives on Long Island. Works full-time at a tech startup. Runs a side consulting business doing AI automation for real companies. Builds products, tools, and experiments on nights and weekends.
			</p>
			<p class="text-muted">He uses AI for all of it.</p>
			<div class="grid gap-6 md:grid-cols-2">
				<div class="rounded-xl border border-border/50 bg-surface p-6">
					<h4 class="mb-3 text-sm font-bold tracking-wide text-accent-light uppercase">For clients</h4>
					<p class="text-sm text-muted">Document intelligence pipelines for automotive financial data. AI-powered brand sites. Automation systems that save companies dozens of hours per week.</p>
				</div>
				<div class="rounded-xl border border-border/50 bg-surface p-6">
					<h4 class="mb-3 text-sm font-bold tracking-wide text-accent-light uppercase">For family</h4>
					<p class="text-sm text-muted">A bedtime story generator with mindfulness themes. An activity generator for parents who need ideas fast. A birthday coordination app that replaced 47 text threads.</p>
				</div>
				<div class="rounded-xl border border-border/50 bg-surface p-6">
					<h4 class="mb-3 text-sm font-bold tracking-wide text-accent-light uppercase">For the internet</h4>
					<p class="text-sm text-muted">BookmarkIQ (Chrome extension for Twitter bookmarks). Retell (AI video repurposing). A handful of open-source tools used by thousands.</p>
				</div>
				<div class="rounded-xl border border-border/50 bg-surface p-6">
					<h4 class="mb-3 text-sm font-bold tracking-wide text-accent-light uppercase">For fun</h4>
					<p class="text-sm text-muted">A hand-tracking particle system. An AI search engine using spatial metaphors. An AI operator named Cortana that runs 24/7 on a server and manages half his life.</p>
				</div>
			</div>
			<p class="text-center text-muted">
				The point is range. Not "AI for marketing" or "AI for developers." AI for everything. That range is what the community is built on.
			</p>
		</div>
	</div>
</section>

<!-- Founding Members -->
<section id="founding" class="relative border-t border-border/50 bg-deep py-20 md:py-28">
	<div class="pointer-events-none absolute inset-0 bg-[radial-gradient(ellipse_at_bottom,_var(--color-accent-glow)_0%,_transparent_50%)] opacity-10"></div>
	<div class="relative mx-auto max-w-3xl px-6 text-center">
		<h2 class="text-3xl font-bold text-heading md:text-4xl">
			50 founding spots. $29/mo locked forever.
		</h2>
		<p class="mx-auto mt-6 max-w-xl text-lg text-muted">
			The first 50 members pay $29/mo. That price never changes for them, regardless of what happens next. After 50 founding members, the price goes to $49/mo.
		</p>
		<div class="mx-auto mt-10 max-w-md rounded-2xl border border-accent/30 bg-surface p-8">
			<div class="mb-6">
				<span class="text-sm font-semibold tracking-wide text-accent-light uppercase">Founding Member</span>
				<div class="mt-2 flex items-baseline justify-center gap-1">
					<span class="text-5xl font-extrabold text-heading">$29</span>
					<span class="text-lg text-muted">/mo</span>
				</div>
				<p class="mt-1 text-sm text-muted">Locked forever. Never increases.</p>
			</div>
			<ul class="mb-8 space-y-3 text-left text-sm text-text">
				{#each foundingPerks as perk}
					<li class="flex gap-3">
						<span class="mt-0.5 text-accent-light">&#10003;</span>
						{perk}
					</li>
				{/each}
			</ul>
			<a
				href="#"
				class="block w-full rounded-xl bg-accent px-6 py-4 text-center text-lg font-bold text-white shadow-lg shadow-accent-glow/25 transition hover:bg-accent-glow hover:shadow-accent-glow/40"
			>
				Lock in your founding spot
			</a>
			<p class="mt-3 text-xs text-muted">Cancel anytime. No contracts.</p>
		</div>
		<p class="mt-8 text-sm text-muted">
			The library grows every week. The value compounds. The price only goes up.
		</p>
	</div>
</section>

<!-- FAQ -->
<section class="py-20 md:py-28">
	<div class="mx-auto max-w-3xl px-6">
		<h2 class="mb-12 text-center text-3xl font-bold text-heading md:text-4xl">
			Questions
		</h2>
		<div class="space-y-3">
			{#each faqs as faq, i}
				<button
					onclick={() => toggleFaq(i)}
					class="w-full rounded-xl border border-border/50 bg-surface px-6 py-5 text-left transition hover:border-accent/20"
				>
					<div class="flex items-center justify-between">
						<span class="font-semibold text-heading">{faq.q}</span>
						<span class="ml-4 text-muted transition-transform {openFaq === i ? 'rotate-45' : ''}">+</span>
					</div>
					{#if openFaq === i}
						<p class="mt-4 text-sm leading-relaxed text-muted">{faq.a}</p>
					{/if}
				</button>
			{/each}
		</div>
	</div>
</section>

<!-- Final CTA -->
<section class="border-t border-border/50 bg-deep py-20 md:py-28">
	<div class="mx-auto max-w-3xl px-6 text-center">
		<h2 class="text-3xl font-bold text-heading md:text-4xl">
			Real work. Real assets. Real community.
		</h2>
		<p class="mx-auto mt-4 max-w-xl text-lg text-muted">
			Join 50 founding members getting the full library, partner perks, and direct access for $29/mo. That price is gone once the spots fill.
		</p>
		<a
			href="#founding"
			class="mt-8 inline-flex items-center rounded-xl bg-accent px-8 py-4 text-lg font-bold text-white shadow-lg shadow-accent-glow/25 transition hover:bg-accent-glow hover:shadow-accent-glow/40"
		>
			Become a Founding Member
		</a>
	</div>
</section>

<!-- Footer -->
<footer class="border-t border-border/50 py-10">
	<div class="mx-auto flex max-w-6xl flex-col items-center gap-4 px-6 text-sm text-muted md:flex-row md:justify-between">
		<span>BuildsByBen &copy; {new Date().getFullYear()}</span>
		<div class="flex gap-6">
			<a href="https://x.com/xBenJamminx" target="_blank" rel="noopener" class="transition hover:text-heading">X / Twitter</a>
			<a href="https://buildsbyben.com" target="_blank" rel="noopener" class="transition hover:text-heading">Portfolio</a>
			<a href="https://github.com/buildsbyben" target="_blank" rel="noopener" class="transition hover:text-heading">GitHub</a>
		</div>
	</div>
</footer>
