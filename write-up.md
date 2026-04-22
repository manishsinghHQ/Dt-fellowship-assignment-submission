# Write-Up: Design Rationale for the Daily Reflection Tree

## Why These Questions

The hardest constraint in this design was the "no free text" requirement — because the obvious failure mode is writing options that are really just four ways to say the same thing, or options so obviously "good" that every rational person picks the same one. Fake choices. Survey questions, not conversation.

I spent most of my time trying to avoid that.

**Axis 1 (Locus of Control)** opened with the hardest calibration problem: how do you get someone to honestly report their first instinct — the one before the rationalisation kicks in? The first question ("where did your mind go first?") uses quoted self-talk deliberately. "What can I do differently?" reads differently than "I adapted" — both are internal locus, but one is reflective and one is action-oriented. The tree branches the same way from both, but asking the follow-up question about *attribution when things went well* (A1_Q3_INT) catches something Dweck's research highlights: growth mindset people credit effort and strategy even when things succeed, while fixed mindset people sometimes attribute success to luck or innate ability. I wanted the tree to probe both failure and success to get a more honest axis reading.

The external branch (A1_Q2_EXT) takes a different tack: instead of more questions about what happened, it asks one precise question — "was there a small moment of choice?" This is drawn from Viktor Frankl's insight (adjacent to Rotter's work) that agency isn't about controlling circumstances, it's about finding the response inside them. Answer "yes, and I took it" routes to a different reflection than "not really." The tree doesn't moralize the external route — it just surfaces the choice that was almost invisible.

**Axis 2 (Contribution vs Entitlement)** was the most psychologically delicate. Entitlement, as Campbell et al. describe it, is invisible to the person holding it. You can't ask "are you entitled?" You have to ask around the edges. The opening question ("what was most on your mind during that interaction?") doesn't mention entitlement at all — it just asks about focus, and the options reveal orientation: self-focused vs. other-focused. The "I'm not sure I gave that much, honestly" option on the entitlement branch gets a completely different reflection from the others — because that's a rare and valuable honesty, and the tree should recognize it differently. Shaming it with the same reflection as someone in denial would be wrong.

**Axis 3 (Radius of Concern)** uses Maslow's hierarchy of concern — the options literally progress from narrow to wide: just me → my team → a specific colleague → the end user/mission. This isn't an accident. The branching then probes whether that orientation was *conscious* or *retrospective* — because someone who held the team in mind while solving the problem is doing something different from someone who only notices it in reflection. Both are worth validating, but differently.

---

## How I Designed the Branching

The core trade-off was **depth vs. breadth**. A fully branching tree (every option leads to a unique path) would require exponential nodes and would be impossible to tune. A fully linear tree (all paths converge immediately) would be dishonest — the tree would pretend to branch but actually just feed everyone the same conversation.

I chose a **hybrid**: branch meaningfully at the axis level (high/low agency routes through different follow-up questions), then converge at reflections before the bridge. This means the tree has ~3 genuinely distinct paths per axis (high, medium, notable-exception), and the reflections themselves are distinct — but then everyone meets at the same bridge before the next axis. The summary node does the heavier work of synthesizing the path taken.

The summary templates are keyed on a 3-axis combination string (e.g., "internal+contribution+other"), giving 12 distinct summaries. These aren't generated — they're authored. Every combination was written separately to say something specific about that *combination*, not just three independent observations concatenated.

**Signal tallying** is kept simple: each question on the internal/contribution/other path adds +1 to that pole's tally. The dominant signal drives the summary key. This is deliberately lossy — nuance is already in the reflection nodes on the way through. The summary is synthesis, not re-scoring.

---

## Psychological Sources That Informed the Design

- **Rotter (1954)**: Locus of Control. The internal/external distinction is the backbone of Axis 1. The key insight I used: locus isn't about outcomes, it's about *causal attribution*. The questions probe where the employee looks for explanation, not just what happened.

- **Dweck (2006)**: Growth vs. Fixed Mindset. Used most explicitly in A1_Q3_INT — asking about attribution when things succeed, not just when they fail. Growth mindset people tend to credit process; fixed mindset people oscillate between "I'm naturally good at this" and "I got lucky."

- **Campbell et al. (2004)**: Psychological Entitlement Scale. The defining feature of entitlement in their work is *independence from contribution* — entitled people feel deserving regardless of what they've done. This informed why the Axis 2 questions probe *what the person's attention was on*, not what they claim they deserve.

- **Organ (1988)**: Organizational Citizenship Behavior. The "did you do something that wasn't technically your job?" question in A2_Q2_CON is almost a direct operationalization of OCB — discretionary effort beyond formal role requirements.

- **Maslow (1969)**: "The Farther Reaches of Human Nature." Maslow's late work on self-transcendence — the idea that the healthiest humans shift their frame from "what do I need?" to "what does the world need from me?" — is the psychological foundation for Axis 3. The radius metaphor (narrow to wide) is mine, but the progression from self-actualization to self-transcendence is his.

- **Batson (2011)**: Perspective-taking. The distinction between imagining how *you* would feel in another's situation vs. imagining how *they* actually feel informed how I wrote the Axis 3 options — particularly the distinction between "a specific colleague who had it harder than me" and "the person or group we're ultimately serving."

---

## What I'd Improve With More Time

**More question nodes.** The assignment minimum is 8; I hit that, but a real product would want 12-15. Specifically, I'd want more nuance in the *middle* of each axis — the current tree is fairly binary (high/low), and real humans often sit in genuine uncertainty that the current options don't fully honor.

**A "stuck" path.** Right now, if someone picks the same "external/entitlement/self" options all the way through, the summary is honest but might land as bleak. I'd add a dedicated recovery reflection for that path — something that names the heaviness without making it heavier.

**Cross-axis memory.** The current interpolation uses individual answers by node ID. A more sophisticated version would let reflections reference patterns across axes — "You mentioned feeling scattered earlier, and you also noticed how much was outside your control. Those aren't unrelated." This requires more complex state but produces much richer reflections.

**Pacing controls.** A 7pm reflection tool needs to feel different on a Monday than a Friday. Some employees might want a 3-minute pass, others a 10-minute sit. The tree doesn't currently have branching for depth preference — I'd add an optional "go deeper" branch after each reflection.

**Streak/pattern awareness.** The tree is stateless across sessions right now. With localStorage or a minimal backend, the summary could compare today's axis readings against last week. "You've leaned external on agency three days this week. What's happening?" That's a product, not just a tool.
