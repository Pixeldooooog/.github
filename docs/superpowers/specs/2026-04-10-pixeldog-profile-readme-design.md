# Pixeldog Profile README Design

**Date:** 2026-04-10
**Owner:** Pixeldog profile repository
**Status:** Approved in chat, pending final written-spec review

---

## Goal

Create a distinctive GitHub profile homepage for `Pixeldog` that feels world-weary, philosophical, and visually restrained rather than promotional. The page should use a small number of dynamic elements to create motion and credibility without collapsing into a generic widget wall.

## Creative Direction

The chosen direction is `Manifesto Noir`.

This profile should read like a personal manifesto rendered as a GitHub homepage:

- cold, precise, and literary
- skeptical of hype and empty optimism
- technically credible without sounding like a resume
- visually minimal, with motion used as atmosphere rather than spectacle

The page should feel like a dark exhibition label or a short editorial note, not a developer landing page.

## Audience

The profile should work for:

- other developers browsing the account
- collaborators evaluating taste and seriousness
- casual visitors who need to understand the account's identity in a few seconds

The page does not need to optimize for hiring-language, conversion language, or broad self-introduction.

## Content Strategy

The README will be structured in five layers:

1. **Opening line**
   - a short manifesto-level sentence that immediately defines tone
   - no "Hi, I'm..." intro

2. **Identity block**
   - 3 to 5 short lines about code, taste, silence, systems, and motive
   - should sound reflective, not melodramatic

3. **Dynamic sentence block**
   - use a typing animation to rotate a few short lines
   - lines should reinforce worldview, not list skills

4. **Proof block**
   - add restrained GitHub stats so the page still feels alive and real
   - keep quantity low to avoid dashboard energy

5. **Atmospheric footer**
   - use a snake animation based on contribution history
   - treat it as a moving artifact, not as a productivity trophy

## Components

### 1. README copy

The README copy should be rewritten from the current draft into a cleaner final version with tighter phrasing and stronger hierarchy.

Copy principles:

- short sentences
- low warmth, high clarity
- no motivational language
- no exaggerated darkness
- no jargon-heavy "builder/creator/innovator" phrasing

### 2. Typing animation

Use `DenverCoder1/readme-typing-svg`.

Purpose:

- introduce controlled motion near the top of the page
- rotate philosophical one-liners
- make the profile feel alive without relying on bright visuals

Example line themes:

- silence and structure
- distrust of noise
- systems and motive
- building as resistance to emptiness

### 3. GitHub stats

Use `anuraghazra/github-readme-stats`.

Scope:

- one main stats card
- optionally one compact language card if spacing supports it

Style constraints:

- dark or monochrome palette
- no loud icon colors
- no excessive badge stacks around it

### 4. Snake animation

Use `Platane/snk`.

Implementation:

- add a GitHub Actions workflow that generates the snake SVG on a schedule and on demand
- publish output to a branch or path suitable for README embedding

Style goal:

- dark theme variant preferred
- positioned near the bottom as a closing visual gesture

### 5. Skills or badges

Use sparingly.

If included at all, use a very small `skill-icons` line with only the most representative tools. This is optional and should be removed if it weakens the page's restraint.

### 6. WakaTime integration

Explicitly out of scope for first pass.

Reason:

- requires ongoing maintenance and external setup
- adds noise before the identity layer is finished

## File Plan

### Files to modify

- `README.md`
  - final homepage content and embedded components

### Files to create

- `docs/superpowers/specs/2026-04-10-pixeldog-profile-readme-design.md`
  - this design record
- `.github/workflows/` workflow file for snake generation
  - scheduled automation for animated contribution asset

## Behavior and Rendering Notes

- The README must still look coherent even if a third-party badge or stats service is temporarily unavailable.
- The top section should remain readable in plain Markdown source view.
- Dynamic blocks must not dominate the page length.
- The page should still feel authored if visitors are viewing from mobile or narrow widths.

## Risks

1. **Over-styling**
   - Too many widgets will make the profile feel derivative.

2. **Tone drift**
   - Copy can easily become performative or adolescent if pushed too hard.

3. **Third-party dependency fragility**
   - Stats and typing widgets rely on external services.

4. **Empty-profile mismatch**
   - Because the account is new, some activity-driven elements may look sparse at first.

## Mitigations

- keep dynamic components to two core pieces plus optional stats
- make the text block strong enough to carry the page by itself
- prefer popular, well-maintained README components
- use contribution snake as atmosphere, not as evidence of volume

## Success Criteria

This design succeeds if:

- the profile feels distinctive within a few seconds
- visitors can describe the account's taste and temperament after one read
- the page includes motion without turning into a dashboard
- the result is suitable as the first visible identity of a new GitHub account

## Implementation Boundaries

This first pass will not include:

- visitor counters
- trophy walls
- large badge collections
- long project catalogs
- external portfolio links section unless requested later
- auto-updating coding-time metrics

## Approval Record

The user approved the `Manifesto Noir` direction in chat on 2026-04-10 and asked to proceed.
