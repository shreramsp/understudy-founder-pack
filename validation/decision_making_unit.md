# Decision-making unit — who can say no

> **What this is** — the buying unit: user, payer, champion, saboteur, and everyone holding a veto, with what each wants, fears, is moved by, and kills deals with.
> **Why it exists** — [../strategy/personas.md](../strategy/personas.md) covers who *benefits*. This covers who can *stop it*, which is what actually stalls deals — and for this product two of the vetoes are unusual: they sit below the buyer and outside the company.
> **How to read it** — the two non-obvious rows are Ray and Sonia. A skeptic should check that each veto has a named artifact that addresses it, not just an acknowledgement.
> **Depends on / feeds** — inherits [../strategy/sales_roadmap.md](../strategy/sales_roadmap.md), personas; feeds [get_keep_grow.md](get_keep_grow.md), `narrative/one_pager.md`.

| Role | Who | Wants | Fears | Moved by | Kills the deal with | Artifact that addresses them |
|---|---|---|---|---|---|---|
| **Payer** | Marcus — MSP owner/COO | Take clients he can't staff; protect margin on new logos | Buying a science project; his engineers' knowledge becoming someone else's asset | His own hours arithmetic, in his own numbers | "Not this quarter" | The engineer-hours ROI calculator (low-fi MVP) |
| **Champion** | Dana — service delivery manager | A runbook that stays true; fewer escalations | Her team not using it, and it becoming her problem | Deviation review that takes 40 minutes a month, not eight hours | "My team won't use it" | The environment dashboard (UX1) and the deviation queue (UX8) |
| **User** | Priya — tier-1 | To not be the newest person in the room at every client | Being trained out of a job | Client-specific procedure where there was a generic runbook | Nothing directly — but her non-use is invisible | Attribution, and the escalation path staying hers |
| **Saboteur / veto from below** | Ray — principal engineer | Fewer repeat interruptions; not to clean up after a third failed automation | A black box acting wrongly in production with his name on it | Reading a skill built from his own session and finding it right; **E2 against a fair baseline** | One credible "this is RPA again" in the team channel — and quiet non-cooperation with capture, which no dashboard shows | Readable `SKILL.md`, rejection without justification (UX6), the E2 result |
| **External veto** | Sonia — client-side IT director, **one per client environment** | To know what leaves her environment | Recordings of her admins somewhere she can't see | The two-stage boundary stated precisely: her recordings stay in her MSP's control, nothing identifying her tenant reaches the vendor | A security review that never ends | The tenant-isolation document, the boundary attestation (UX10), and — when it exists — **X25's adversarial result** |
| **Silent veto** | The MSP's own insurer / compliance advisor | Defensible risk posture | An AI principal with write access to client tenants | Destructive-action gating that is not configurable off; agent identity in the client's own audit log | An exclusion or a premium loading | Action-class policy (X5), audit export (X21) |

## The three things this table says that the persona cards do not

**1. Two vetoes sit outside the reporting line, and both concern the recording rather than the product.** Ray is below the buyer; Sonia is outside the company entirely and there are ~41 of her per customer. **A deal signed by Marcus can fail three times over**, and the failures look nothing alike: Ray's is silent, Sonia's is a stalled review, the insurer's is a clause.

**2. Ray's veto has no detector.** Every other row fails loudly. Ray's failure mode is *disuse* [S36] — he stops narrating, pauses capture more, and the library quietly learns only the easy procedures. It presents as slow adoption. **E6 exists solely to instrument this**, and it is the only reason a capture-rate metric is worth collecting.

**3. Sonia recurs, which makes her a throughput constraint rather than a gate.** One review per environment at ~6 weeks means expansion velocity is set by review capacity, not sales capacity — which is why `strategy/market_sizing.md`'s ramp is paced the way it is, and why `business_model_canvas.md`'s customer-relationship hypothesis tests review cycle time rather than sales touches.

**Recommended next 3:** (1) write the tenant-isolation document before the first pilot conversation — it addresses the veto with the longest cycle time; (2) put E2's result in front of a Ray-profile engineer before any deal, since the persona who converts hardest also converts most durably; (3) ask Q19 of the discovery guide in every owner conversation — the external veto is invisible until someone asks the buyer what their client would say.
