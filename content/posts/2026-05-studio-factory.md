---
title: "Beyond Studio and Factory"
date: 2026-05-10T00:00:00Z
draft: false
categories: ['AI', 'Humans', 'Org Design']
---

*I'm think about org design when agents do the work.*

![Unsplash | Katja Ano](/katja-ano-_7ceGXTAtyQ-unsplash.jpg)

Two patterns are showing up in how teams reorganise around AI. The **studio**: humans and agents working hand-in-glove, the org as creative atelier, judgment applied turn by turn. The **factory**: an army of autonomous agents producing at scale, with humans pulled back to design the line, set the rules, and handle exceptions.

The names are useful and they reach at something real. They also make the situation look more novel than it is. Nothing about the underlying problem is new. But the lens through which we see it has to shift — and that shift is where all the difficulty lives.

## The variables were always there

Every org has always had to handle three things, whether or not it called them out. **Supervision cadence**: how often human judgment touches the work. **Coordination topology**: who talks to whom — star, mesh, or hierarchy. **Reversibility**: can you undo what was done, and at what cost.

Pre-AI these were mostly handled implicitly. Manager check-ins set cadence. Org charts set topology. Reversibility rarely bound the design because human throughput was slow enough that catastrophic actions had natural friction. With agents none of that holds. Agent throughput outpaces any default cadence, agent-to-agent communication isn't on the org chart, and one bad action ripples through a hundred downstream calls before anyone notices.

The variables are the same; what's changed is they've been forced into the open. Studio names the configuration with tight cadence, star topology, reversibility moot. Picture a senior engineer pair-coding with an AI on a complex refactor — every diff reviewed before it lands, every decision flowing through the human, errors caught at the keystroke. Or an analyst working a deal screen, the AI surfacing comparables and stress tests, the human deciding what's signal and what's noise. The throughput is bounded by the human's attention and that's the point.

Factory names the configuration with loose cadence, mesh topology, and work that's either reversible or has explicit gates where it isn't. Picture a contract review pipeline parsing thousands of agreements overnight, with humans reviewing only flagged exceptions and aggregate quality metrics. Or an agentic SDLC generating ninety per cent of pull requests autonomously, where the human reviews at the PR level rather than the keystroke. The work has to be reversible — code rolls back, extractions re-run — or external commitments and money movements sit behind explicit human approval.

Most early pain will come from picking these incoherently. The classic failure: an agentic outbound email pipeline sending thousands of messages to enterprise prospects with no human review. One bad pattern — wrong tone, wrong segment, factual error in the pitch — burns the prospect list before anyone notices. Loose cadence on irreversible work. The configuration looks like a factory but the work shouldn't be in factory mode at all.

That's the design problem. Old problem, made impossible to handle implicitly by the new throughput. So far, nothing new.

## The unit of analysis has to change

What is new is that the relevant unit of analysis is no longer the human or the agent. It's the *human+AI pairing*.

People still talk about "the team" or "the agent fleet" as separable things. They aren't, once agents are stitched into the work. The thing that produces output is the seam — a human carrying calibration responsibility for some bounded set of agent activity. You can't analyse the human alone (their direct output is no longer the relevant measure) or the AI alone (it has no standing to act on its own). The unit is the pairing, and the relevant questions are about that pairing: how many agents per human, what does the seam look like, who is the human, what is the agent doing on its own, where is the human inserted.

This reframes the studio/factory question. The org isn't picking between two shapes. It's deciding, per stream of work, the shape of the human+AI unit and how those units stitch together. Studio is high human density per unit of throughput. Factory is low. Both are configurations of the same underlying unit, with the cadence/topology/reversibility variables tuned differently inside each.

The shift looks small but it changes how the design work feels. You stop asking "how do we restructure the org for AI" and start asking "what's the right human+AI unit for this stream, and who is the human in it."

## Why humans, still

The cliché is that humans bring judgment and taste. That's not a mechanism. Taste in isolation is plausibly automatable.

The non-cliché version is that taste requires being a target of consequences. Agents don't carry skin in the game. They can't be fired, sued, demoted, or remembered for a bad call three years later. They don't have a reputation that compounds. When a human+AI unit ships something that hurts a customer, the consequences attach to the human side of the unit, because nothing else in the system has standing to be held accountable.

That's the asymmetric thing. The human in the unit is doing three things the agent can't.

The first is calibrating against the agents being wrong even when they look right. Picture the engineer reviewing an AI-generated PR that compiles, passes tests, and reads cleanly — but uses an internal API the agent didn't know was on its way out, or follows a pattern the team agreed last quarter to stop using. The artefact is plausible. The reviewer's catch comes from context the agent never had. Or the analyst scanning an AI-generated valuation and knowing from three prior deals in the same submarket that the comp set is plausible but wrong. The signal isn't in the output; it's in the gap between what the output looks like and what the reviewer knows the agent didn't.

The second is carrying the accountability that consequences attach to. When the deprecated API breaks production, when the bad valuation gets used in a deal that loses money, when the autonomous email pattern burns a prospect list, those consequences land somewhere — and the somewhere has to be a human, because nothing else in the system has standing to be held responsible.

The third is exercising judgment about where the agents can be pointed and where they have to be gated. Which streams sit safely in factory mode. Which need studio supervision. Where the seams have to be. This is the meta-judgment that determines whether the other two ever get exercised in the right places.

These three are connected. You can only calibrate well if you carry the consequences of being wrong. You can only set boundaries well if you've internalised the calibration. The skin-in-the-game asymmetry isn't separable from the judgment claim — it's the precondition for it.

So "best orgs are run by best humans" isn't romantic. The constraint on org quality is the calibration-bearing capacity of the humans inside the human+AI units. The engineer who catches the deprecated API in seconds is doing the same job as the analyst spotting the wrong comp set, as the support lead who notices a cluster of agent escalations all pointing at a product bug the agents didn't flag. Hire well there and the agent throughput becomes useful work. Hire poorly and it becomes liability at scale.

## Nothing new, everything new

Studio and factory point at two coherent shapes in a familiar design space. The variables underneath them are old. Every org has always had to handle cadence, topology, and reversibility, and every org has always relied on humans as the load-bearing element for accountability and judgment. None of that has changed.

What's changed is the lens. The unit of analysis is no longer the human team or the agent stack as separate things. It's the human+AI unit, and the org is a fabric of those units stitched together. The principles haven't moved. The discipline of seeing the work through the new unit, and staffing the human side of it accordingly, is where the difficulty has migrated.

Get the lens right and the rest follows. Keep using the old one — humans here, AI there — and no agent count will save the org.
