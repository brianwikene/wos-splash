<script lang="ts">
	import {
		Backpack,
		CalendarCheck,
		HeartHandshake,
		Plus,
		Send,
		Shield,
		Users
	} from '@lucide/svelte';
	import { onMount } from 'svelte';

	let visible = $state(false);

	onMount(() => {
		const t = setTimeout(() => (visible = true), 60);
		return () => clearTimeout(t);
	});

	// Keeping this for later when you re-enable the form
	let email = $state('');

	function handleSubmit(e: SubmitEvent) {
		e.preventDefault();
		alert(`Thanks for subscribing with: ${email}`);
		email = '';
	}
</script>

<main class:visible>
	<div class="shell">
		<header class="header">
			<div class="mark" aria-hidden="true">
				<Plus size={22} />
			</div>

			<h1 class="title">
				Serve people well.<br />
				<span class="highlight">TOGETHER.</span>
			</h1>

			<p class="subtitle">
				WorshipOS is a calm system for planning gatherings, caring for people, and coordinating
				volunteers — without the noise.
			</p>
			<p class="subtitle subtitle--tight">Built for clarity and compassion, not complexity.</p>

			<!--
			<form class="email-form" onsubmit={handleSubmit}>
				<label class="sr-only" for="email">Email address</label>
				<input
					id="email"
					type="email"
					placeholder="Enter your email"
					bind:value={email}
					required
					class="email-input"
				/>
				<button type="submit" class="submit-btn">Get Early Access</button>
			</form>
			-->
		</header>

		<section class="features" aria-label="Core Philosophy">
			<article class="feature">
				<div class="feature-icon" aria-hidden="true">
					<CalendarCheck size={26} />
				</div>
				<h3>Gather</h3>
				<p>
					<em>From scattered notes to shared clarity.</em> Plan gatherings with intention. Everyone sees
					the same flow, roles, and resources.
				</p>
			</article>
			<article class="feature">
				<div class="feature-icon" aria-hidden="true">
					<Users size={26} />
				</div>
				<h3>Know</h3>
				<p>
					<em>People, stories, and context in one place.</em>
					Track relationships, needs, and rhythms — because ministry happens between Sundays.
				</p>
			</article>
			<article class="feature">
				<div class="feature-icon" aria-hidden="true">
					<HeartHandshake size={26} />
				</div>
				<h3>Shepherd</h3>
				<p>
					<em>Care that notices and follows through.</em> Capture needs, prayer, and next steps so no
					one is overlooked.
				</p>
			</article>
			<article class="feature">
				<div class="feature-icon" aria-hidden="true">
					<Backpack size={26} />
				</div>
				<h3>Equip</h3>
				<p>
					<em>Resources ready when teams prepare.</em> Songs, files, and guidance organized so people
					can serve with confidence.
				</p>
			</article>
			<article class="feature">
				<div class="feature-icon" aria-hidden="true">
					<Send size={26} />
				</div>
				<h3>Send</h3>
				<p>
					<em>Clear roles. Timely reminders.</em> Invite, schedule, and confirm volunteers so teams arrive
					ready and unhurried.
				</p>
			</article>
			<article class="feature">
				<div class="feature-icon" aria-hidden="true">
					<Shield size={26} />
				</div>
				<h3>Sustain</h3>
				<p>
					<em>Healthy teams last.</em> Scheduling honors limits, shares the load, and prevents burnout.
				</p>
			</article>
		</section>

		<footer class="footer">
			<p>&copy; 2026 WorshipOS. All rights reserved.</p>
		</footer>
	</div>
</main>

<style>
	:global(body) {
		margin: 0;
		background: linear-gradient(135deg, #f5f1e8 0%, #e8e3d6 100%);
		color: #3a3a3a;
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
	}

	/* Subtle warm ambient glow */
	:global(body)::before {
		content: '';
		position: fixed;
		top: -260px;
		right: -260px;
		width: 620px;
		height: 620px;
		background: radial-gradient(circle, rgba(139, 115, 85, 0.08), transparent 68%);
		z-index: -1;
		pointer-events: none;
	}

	main {
		min-height: 100vh;
		display: grid;
		place-items: center;
		padding: 2.5rem 1.25rem;
		opacity: 0;
		transform: translateY(12px);
		transition:
			opacity 500ms ease-out,
			transform 500ms ease-out;
	}

	main.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.shell {
		width: min(1060px, 100%);
		background: rgba(255, 255, 255, 0.7);
		backdrop-filter: blur(10px);
		border-radius: 18px;
		padding: 3.5rem 2.5rem;
		box-shadow: 0 10px 30px rgba(90, 74, 58, 0.12);
		border: 1px solid rgba(139, 115, 85, 0.15);
	}

	.header {
		text-align: left;
	}

	.mark {
		width: 52px;
		height: 52px;
		border-radius: 999px;
		display: grid;
		place-items: center;
		background: linear-gradient(135deg, #8b7355 0%, #a68a6d 100%);
		color: #ffffff;
		border: 1px solid rgba(139, 115, 85, 0.2);
		margin-bottom: 1.75rem;
	}

	.title {
		margin: 0 0 1.25rem 0;
		font-size: 3.25rem;
		line-height: 1.05;
		font-weight: 750;
		letter-spacing: -0.02em;
		color: #4a3f35;
	}

	.highlight {
		color: #8b7355;
		font-weight: 400;
	}

	.subtitle {
		max-width: 58ch;
		margin: 0 0 1rem 0;
		font-size: 1.15rem;
		line-height: 1.7;
		color: #6a5f55;
	}

	.subtitle--tight {
		margin-bottom: 0;
	}

	.features {
		margin-top: 3rem;
		display: grid;
		grid-template-columns: repeat(3, minmax(0, 1fr));
		gap: 1.75rem;
	}

	.feature {
		border-radius: 16px;
		padding: 1.5rem 1.25rem;
		background: rgba(255, 255, 255, 0.5);
		border: 1px solid rgba(139, 115, 85, 0.12);
		transition:
			transform 180ms ease,
			background 180ms ease,
			box-shadow 180ms ease;
	}

	.feature:hover {
		background: rgba(255, 255, 255, 0.75);
		transform: translateY(-2px);
		box-shadow: 0 8px 24px rgba(90, 74, 58, 0.15);
	}

	.feature-icon {
		width: 56px;
		height: 56px;
		border-radius: 14px;
		display: grid;
		place-items: center;
		margin-bottom: 1rem;
		background: rgba(139, 115, 85, 0.08);
		border: 1px solid rgba(139, 115, 85, 0.15);
	}

	.feature-icon :global(svg) {
		color: #8b7355;
		stroke-width: 1.75;
	}

	.feature h3 {
		margin: 0 0 0.5rem 0;
		font-size: 1.1rem;
		font-weight: 650;
		color: #4a3f35;
	}

	.feature p {
		margin: 0;
		color: #6a5f55;
		line-height: 1.65;
		font-size: 0.98rem;
	}

	.footer {
		margin-top: 3rem;
		padding-top: 1.5rem;
		border-top: 1px solid rgba(139, 115, 85, 0.15);
		text-align: center;
		color: #8b7355;
		font-size: 0.95rem;
	}

	@media (max-width: 900px) {
		.shell {
			padding: 3rem 1.75rem;
		}
		.title {
			font-size: 2.6rem;
		}
		.features {
			grid-template-columns: 1fr;
		}
	}
</style>
