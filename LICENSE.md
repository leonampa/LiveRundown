# LiveRundown License (Free Forever License)

**Summary (not a substitute for the full terms below):** LiveRundown is free, permanently, for everyone — individuals, schools, theaters, businesses, anyone. You can use it, modify it, and host it. You can charge for *your own labor* (setup, hosting infrastructure, customization, training) — but never for the software itself, whether standalone or as part of something else, and never with ads, tiers, or paywalls. Forks must carry this same license forward and must credit the original project. No trademark is claimed, but the name can't be used to imply endorsement of unrelated or non-compliant products. That's the deal.

**A practical note, not a legal one:** you don't actually need to pay anyone to run LiveRundown. Firebase's free tier and Netlify's free tier are, at the time of writing, more than sufficient to host and sync the Software for the vast majority of individuals, schools, and small productions. If someone is charging you for "access" to LiveRundown itself, that's very likely a violation of Section 2 — check the free-tier options above before paying anyone for the software.

---

## 0. Definitions

To keep this license enforceable and clear, the following terms are used consistently throughout:

- **"the Software"** means LiveRundown, including its source code, assets, and any substantial or functionally significant part thereof, in original or modified form. Incorporating a small, incidental snippet of code from LiveRundown (for example, a single short utility function) into an otherwise unrelated project does not, by itself, make that unrelated project a "derivative work" subject to this license — but reproducing or reimplementing LiveRundown's core functionality (its script-sync engine, rundown/cue logic, or the substance of what makes it work as an AutoCue-style tool), whether copied directly or closely re-derived, does count as the Software for purposes of this license, regardless of what it is embedded in or renamed to.
- **"Modified version" / "derivative work"** means a version of the Software that has been changed from the original in a way that affects its functionality, behavior, structure, or code — including added or removed features, changed logic, changed dependencies, or reorganized code. This license's obligations (attribution, share-alike, no-charge) apply to any such modified version, regardless of how small the functional change is. **Purely cosmetic edits with no functional effect** — for example, renaming an internal variable, adjusting colors, fonts, spacing, or wording, or reformatting code — do not by themselves make a copy a "modified version" requiring share-alike re-licensing, provided attribution (Section 6) is still retained. If there is a genuine doubt about whether a change is functional or purely cosmetic, Section 11 (interpretation in favor of keeping the Software free) governs.
- **"Instance"** means any running or deployed copy of the Software, whether hosted online, run locally, or embedded in another product or workflow.
- **"You" / "licensee"** means any person or entity exercising any right granted under Section 1, including using, copying, modifying, hosting, or redistributing the Software or a derivative work.
- **"Charging for the Software"** means requiring payment, subscription, or any other consideration (i) in exchange for the Software itself, a copy of it, or a license to use it; (ii) in exchange for access to any instance of it; or (iii) as a condition of accessing a paid product, platform, or service whose value to the customer substantially depends on the Software's functionality — regardless of whether the Software is marketed, itemized, or named separately in that transaction. See Section 3 for what is explicitly exempted from this (labor, hosting costs, and genuinely third-party services).
- **"Substantially depends"** means that the Software's functionality is a primary reason a reasonable customer would pay for the offering — not merely a convenience, a nice-to-have, or one tool among many with independent value. In deciding whether a paid offering's value substantially depends on the Software, relevant factors include: whether the offering would still be marketable and useful to its customers with the Software's functionality removed; whether the Software is one of many roughly co-equal components (as opposed to the centerpiece); how the offering is marketed (e.g., whether the Software's features are advertised as the reason to buy); and whether the price changes meaningfully based on the presence or absence of the Software's functionality. Non-exhaustive examples:
  - **Not substantial dependence (permitted):** A paid production-management platform with scheduling, invoicing, crew management, and a dozen other unrelated tools happens to also embed LiveRundown as one minor feature among many, where the platform's marketing and pricing are not built around it.
  - **Substantial dependence (prohibited):** A paid "AutoCue-style teleprompter/rundown service" that is LiveRundown, or a thin wrapper around it, with a subscription fee added — regardless of what else is bundled alongside it or what it is renamed to.
  - **Ambiguous cases** should be resolved using Section 11 (interpretation in favor of keeping the Software free).

## 1. Grant of Rights

Subject to the conditions below, LiveRundown ("the Software") grants any person or organization — regardless of whether they are an individual, nonprofit, school, or for-profit business — a worldwide, royalty-free, perpetual license to:

- **Use** the Software for any personal, educational, or professional purpose;
- **Copy** the Software;
- **Modify** the Software and create derivative works;
- **Self-host** or deploy the Software, in original or modified form; and
- **Redistribute** the Software, in original or modified form.

No permission beyond what is explicitly granted above is implied. Anything not affirmatively permitted in this license is reserved to the original author.

**Patent grant.** To the extent the original author(s) hold or later acquire any patent rights covering the Software, they grant every recipient a worldwide, royalty-free, non-exclusive license under those patent rights to make, use, and distribute the Software, to the same extent as the rights granted above. This grant does not extend to patent claims that read only on modifications you make yourself, nor to any other product or software you combine with the Software. If any person or entity initiates a patent infringement claim (including a cross-claim or counterclaim) alleging that the Software, or a contribution to it, infringes a patent, that person or entity's rights under this license (including this patent grant) terminate automatically as of the date the claim is filed.

**Irrevocability.** Once this license has been granted for a given copy of the Software, it cannot be revoked for that copy, even if the original author(s) later release future versions of the Software under different terms, transfer the project, or cease maintaining it. Anyone holding a lawfully obtained copy retains their rights under this license for that copy indefinitely, subject only to the termination provisions in Section 9 and the patent-retaliation provision above.

## 2. No Charging for the Software

No person or entity may charge a fee, subscription, or any form of payment for:

- the Software itself;
- a license to use it;
- access to an unmodified or modified instance of it, where the thing of value being sold is the Software's functionality rather than a provider's labor (see Section 3); or
- any individual feature of the Software.

This prohibition applies whether the Software is sold on its own, or embedded, incorporated, or relied upon as a component of a larger paid product, platform, or workflow. If a paid offering's value to its customers substantially depends on the Software's functionality, that counts as charging for the Software, even if the Software itself is not itemized, named, or marketed separately.

There are no "tiers," "editions," or "premium" versions of the Software's own functionality. The Software is provided as a single, complete, free offering — it is not permitted to withhold or paywall any feature as an upsell.

## 3. Permitted: Charging for Labor, Hosting, and Genuinely Third-Party Services

This license does **not** prevent anyone from charging for their own time, skills, or infrastructure costs related to the Software, including:

- installation, configuration, or customization services;
- hosting infrastructure costs (e.g., a Netlify, GitHub Pages, or server bill passed on to a client);
- ongoing maintenance or technical support;
- training; or
- custom hardware integration (e.g., cue-light or peripheral builds) built to work with the Software.

The distinction is: **you may sell your labor and infrastructure. You may not sell the Software, whether alone or as the substantive value inside something else you're selling.** A provider may not condition access to a working copy of the Software on any paid support contract, membership, or service agreement — a person must always be able to obtain and run a free, fully-functional copy without paying anyone.

Fees charged by genuinely independent third parties for their own services (for example, a hosted database or API such as Firebase, billed directly by that provider according to their own pricing) are permitted, since the fee is for the third party's service, not for LiveRundown.

**Modified versions run as a network service.** If you run a modified version of the Software so that others interact with it over a network (for example, as a hosted web app, an API, or a backend-plus-frontend product), you must make the complete, corresponding source code of your modified version available to every user who interacts with it — at no charge, in a form and manner that allows them to run their own copy. This applies even if the user-facing part of your modified version looks or behaves like the free original. A "free-looking" frontend connected to a paid, closed-source, or functionality-enhanced backend is a modified version of the Software for purposes of this license, and is subject to this clause, the no-charge rule in Section 2, and the "substantially depends" test in Section 0.

A hosting or maintenance fee must be reasonably tied to actual infrastructure and labor costs, at rates comparable to what the same infrastructure or labor would reasonably cost from an ordinary third-party provider. A fee that is effectively a per-seat, per-user, or per-instance charge for *access* to the Software — dressed up as a "hosting fee" but not reflecting genuine hosting cost or labor at a comparable market rate — is charging for the Software and is prohibited. A fee that scales primarily with the number of users or instances accessing the Software, rather than with the actual infrastructure load or labor hours involved, is presumed to be a disguised access charge unless the provider can show a genuine cost basis for the scaling.

For the avoidance of doubt: the official instance(s) maintained by the original author(s) (including any hosted on free-tier infrastructure such as GitHub Pages, Netlify, or Firebase) do not become "charging for the Software" merely because the underlying infrastructure provider has its own paid tiers or pricing. Using free-tier infrastructure, or later needing to cover genuine infrastructure costs on official instances at no markup, does not itself violate this license.

## 4. No Advertising

No hosted, modified, or redistributed instance of the Software may display advertising of any kind, whether monetized or unmonetized, including but not limited to banner ads, sponsored content, or affiliate placements.

**Voluntary support is allowed.** A small, clearly optional prompt to support the developer(s) (e.g., a "Buy Me a Coffee," Ko-fi, or GitHub Sponsors link or button) is permitted, provided that:

- it is not a condition of using any feature of the Software;
- it does not unlock, gate, or affect functionality in any way; and
- it is not presented in a way that pressures, interrupts, or nags the user (e.g., no recurring pop-ups or modals demanding payment).

## 5. No Bundling Workaround

The Software may not be bundled into a paid product, kit, platform, or package in a way that uses inclusion of the Software to inflate the price of that offering, or in a way that makes the paid offering's value substantially dependent on the Software's functionality (see Section 2). If the Software is bundled with other paid materials, its inclusion must not be a basis for any part of the price, and a free, standalone copy of the Software must remain available to anyone who wants it independent of the paid bundle.

## 6. Attribution

Any use, hosted instance, or redistribution of the Software — modified or not — must include clear and visible credit, in a location a typical user would reasonably see (e.g., an About/Info screen, footer, or settings panel), reading substantially as follows:

> **LiveRundown** by [@leonampa](https://github.com/leonampa) on GitHub — [leonampa.github.io/liverundown](https://leonampa.github.io/liverundown)

Attribution may not be removed, hidden, obscured, or made disproportionately difficult to find relative to the rest of the interface.

## 7. Derivative Works and Forks (Share-Alike)

Any modified, extended, or derivative version of the Software — including forks with any changes, however small — must:

- carry forward this exact license, unmodified, covering the derivative work in full; and
- retain the attribution required in Section 6.

A derivative work may not be relicensed, sublicensed, or distributed under different or additional terms that would permit anything this license prohibits (including charging for the Software, running ads, or gating features). Modifying, renaming, or rebranding the Software does not exempt a derivative work from these terms.

You are free to rename your fork to anything you like, provided attribution to the original LiveRundown project is retained as described in Section 6. The one exception is that a fork which violates this license (for example, by charging for the Software or running ads) may not continue to use the name "LiveRundown" for that non-compliant version — the name may only be used by instances that remain in compliance with this license.

**Name usage beyond forks.** No formal trademark is claimed in the name "LiveRundown." However, no person or entity — whether or not they have forked or modified the Software — may use the name "LiveRundown," or any name confusingly similar to it, to market, advertise, or describe a different, unrelated, or non-compliant product or service in a way that suggests official origin, sponsorship, or endorsement by the original author(s) where none exists. Accurate, factual references (e.g., "compatible with LiveRundown," "based on LiveRundown," in compliance with Section 6's attribution requirement) are permitted and encouraged.

## 8. No Warranty

The Software is provided "as is," without warranty of any kind, express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, or non-infringement. In no event shall the author(s) be liable for any claim, damages, or other liability arising from the use of the Software, including but not limited to failures during live performances or events.

## 9. Termination

Your rights under this license terminate automatically if you materially violate any of its terms. If you become aware of a violation, your rights are reinstated if you cure the violation (e.g., remove the paywall, ads, or unauthorized terms, and restore attribution) within 30 days of becoming aware of it.

This automatic cure applies the first time you violate this license. If you violate the license a second time after having already cured a prior violation, your rights terminate permanently and are not automatically reinstated by a further cure — reinstatement in that case is at the sole discretion of the original author(s).

This license does not, and cannot, guarantee enforcement — particularly since the Software can be used offline and without any account or check-in. It exists to state the terms clearly, so that any violation is unambiguous, not to promise policing capability the author does not have.

## 10. Contributions

By submitting a contribution (such as a pull request, patch, or code snippet) to the Software, you agree that your contribution is licensed under this same license, and that you have the right to make that grant.

## 11. Interpretation

If any provision of this license is found unenforceable in a given jurisdiction, the remaining provisions remain in full effect. This license is intended to keep LiveRundown free, in price and in spirit, for every individual, team, school, and organization — indefinitely, and to remain accessible in a way that comparable commercial arts/production software (subscription- or tier-gated tools in this space) often is not. Ambiguities should be resolved in favor of that intent.

## 12. Governing Law

This license is governed by the laws of Greece, without regard to conflict-of-law principles. This is stated for clarity and interpretation purposes only. The author's intent is for this license to be self-explanatory and to make violations unambiguous to any reasonable reader, so that disputes can be resolved through direct communication and voluntary compliance rather than legal action. Litigation is a last resort the author hopes never to need, not a goal of this license.

## 13. No Guarantee of Enforcement or Technical Protection

The Software contains no license keys, telemetry, tracking, phone-home checks, or any other technical measure to detect, prevent, or restrict unauthorized use, and can be used fully offline (with sync features unavailable without a user's own backend configuration). The author has no practical means of knowing who uses the Software, how, or whether a given use complies with this license, and does not undertake to monitor, audit, or enforce compliance. The absence of a technical restriction is not permission to violate this license, and a user's ability to use the Software without detection does not affect the validity of this license or the obligations it imposes. This section exists to set expectations, not to limit the rights granted in Section 1.

---

*LiveRundown by [@leonampa](https://github.com/leonampa) — [leonampa.github.io/liverundown](https://leonampa.github.io/liverundown)*
