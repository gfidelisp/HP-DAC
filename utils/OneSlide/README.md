# One-Slide Follow-Up

Project tracking for Hp-DAC. One slide per developer per week — objective,
activities, obstacles, results, next steps.

The format is deliberately small. A slide that cannot hold everything forces
a choice about what matters, and that choice is most of the value.

| File | Use |
|---|---|
| `One-Slide.pptx`, slide 1 | Template with guidance and worked examples — read once |
| `One-Slide.pptx`, slide 2 | Blank working slide — duplicate this one every week |

---

## The cycle

Work runs in **six-week macro cycles** with a **two-week cooldown**.

| Phase | What happens |
|---|---|
| **Kickoff** (day 1) | Group session to map cross-dependencies, then 1:1 with each developer to set the cycle objective and activity list |
| **Weeks 1–6** | Weekly meeting, one slide per developer |
| **Close** (week 6) | Review against the objective: what landed, what didn't, why |
| **Cooldown** (2 weeks) | Papers, reports, conferences, deferred fixes. No cycle commitments |

The cooldown is not slack to be reclaimed. Without it, conference deadlines
and paper revisions leak into the cycle, every objective slips for reasons
nobody planned, and the six-week boundary stops meaning anything.

**Weekly meeting.** Slides circulate 24 hours ahead so nobody reads status
aloud. The meeting opens by reading **last week's NEXT STEPS** — three or
four lines, thirty seconds, each gets a yes or no — then spends its time on
obstacles and decisions. Ten minutes per person.

---

## Filling the slide

### Header — `1. FOLLOW-UP - OWNER`, `DD/MM/AAAA - DD/MM/AAAA`

Sequential number, owner's name, and the week's date range. The number runs
across the whole project so the deck accumulates into an archive:
`2.4` is cycle 2, week 4.

> `2.4 FOLLOW-UP - A. Lorenzoni` · `25/08/2026 - 31/08/2026`

### OBJECTIVE — *what this cycle is for*

**Written at kickoff, unchanged for all six weekly slides.** That constancy
is the point: it is the fixed reference each week is judged against.
Rewriting it is how a cycle quietly becomes whatever happened to get done.

One sentence, stating an outcome with a condition that can be checked.

> Deliver a steady-state model of the commercial heat pump that reproduces
> the measured COP within ±10% over a sink temperature of 60 to 95 °C.

Not *"work on the heat pump model"* — no completion condition, so no week
can ever fail against it.

### ACTIVITIES — *what we agreed to do, and where each item stands*

Three to six items, **fixed at kickoff**. The list is identical every week;
only the formatting changes as items move between states.

| State | Format |
|---|---|
| Done | Light gray, ~~strikethrough~~ |
| In progress | Black |
| Planned | Light gray |

Order them done → in progress → planned. Items migrate upward over the
cycle and the block drains from the bottom, so the slide reads as a
burn-down without anyone drawing one.

**Start every item with a verb**, infinitive or imperative, in the same form
in all three states — *Commission, Validate, Quantify, Fit, Measure, Select,
Decide, Document*. Never conjugate by state: an item must be the same string
in week 2 and week 5 or the eye cannot match it across slides.

A verb forces a completion condition. Avoid *Study, Analyse, Investigate,
Work on, Improve, Explore* — they have no end state and will run the whole
cycle. If the work really is open-ended, write it as a decision:
*"Decide by w5 whether to continue with R1336mzz(Z) or fall back to a
cascade."*

> ~~Fit compressor performance map to manufacturer data~~
> **Commission heat pump on DAC 15TA**
> Validate steady-state model against 60–80 °C tests

The test at kickoff: *what will I look at to agree this is done?* No answer
means the verb is wrong.

### OBSTACLES — *what is in the way to meet the objective*

Obstacles only. Not progress, not a recap of the activities. Two or three
lines — a slide listing six has stopped prioritising.

**The test:** if the developer can clear it alone within the week, it is not
an obstacle, it is an activity that hasn't been done yet.

Each line carries the obstacle, its effect on the objective, who removes it,
and by when. The owner is whoever *can* remove it, which is usually not the
developer.

> Manufacturer data covers only 35–75 °C condensing, leaving the 85–120 °C
> range needed for DAC unsupported by any fit — G. Peixer to request extended
> data or approve extrapolation, by 05/09.

> Heat pump delivery to PUCRS slipped to 15/09, holding commissioning and
> pushing E1 testing about two weeks past the cycle — G. Peixer to decide on
> renting a unit, by 05/09 — *open since w2*.

Keep the *open since* tag on anything carried over. An obstacle in its third
week is a management failure rather than a project fact, and the slide should
say so without anyone having to.

When there is nothing, write **None**. A blank box reads as an unfilled
field, not as a clear week.

### RESULTS — *what do we now know that we didn't last week*

The largest block on the slide: **one figure or table, plus one sentence
saying what it shows.** Evidence, not activity. Data, not narrative.

The sentence states what the evidence *means*, with a number — same
discipline as a figure caption.

> COP falls from 3.4 to 2.1 as the sink temperature rises from 60 to 95 °C;
> the model overpredicts by 8% above 85 °C.

Not *"plot of COP versus sink temperature"*. If no number fits, ask whether
there is a result yet.

**Keep the same figure across the cycle and let it fill in.** A validation
plot that gains points week by week tells the story better than six
unrelated figures, and the week-6 version is the one that goes into the ANP
report.

Generate it at the block size — **125 × 85 mm** — not the 190 mm manuscript
version. Scaled down to fit, 13 pt labels land at about 8.5 pt and are
unreadable on a projector:

```python
fig, ax = plt.subplots(figsize=(125 * MM, 85 * MM))
```

A negative result is a result. A week with no new evidence says so in one
line and leaves the previous figure in place.

### NEXT STEPS — *what will be true at the next meeting*

The coming week only — the rest of the cycle lives in ACTIVITIES. Every line
traceable to an activity, verb-first, with an **owner and a date**.

Filled in **two passes**. Before the meeting, the owner drafts their proposed
steps; that version circulates. During the meeting, team feedback is added to
the same block, and the post-meeting version is the record — save it over the
circulated one so there is a single file per week.

> **Drafted before**
> Repeat the 90 °C test with the recalibrated Coriolis meter — A. Lorenzoni, 03/09.
>
> **Added in the meeting**
> Check the suction-line insulation before rerunning; it may explain the 8%
> overprediction (P. Faria) — A. Lorenzoni, 03/09.

Mark the origin in parentheses. Not for credit — when an assumption turns out
wrong in week 5, the initials point back to the conversation that produced it.

**A suggestion is not a commitment until it has an owner and a date.** Anything
raised is either committed here, or parked into ACTIVITIES as a planned item
or into the next cycle's backlog. Declining to commit is the normal outcome:
a cycle has a fixed appetite, and accepting every suggestion is how six weeks
of work becomes nine.

Two to four lines drafted, six after feedback. Beyond that the week is
oversubscribed.

Someone other than the presenter types during the meeting. People phrase
suggestions more precisely when they can see them being written down.

---

## What changes when

| Block | Set at | Changes |
|---|---|---|
| Header | weekly | number, dates |
| OBJECTIVE | kickoff | never, within a cycle |
| ACTIVITIES | kickoff | formatting only |
| OBSTACLES | weekly | every week |
| RESULTS | weekly | every week |
| NEXT STEPS | weekly | drafted, then extended in the meeting |

Two blocks static, three live. If OBJECTIVE or the ACTIVITIES list changes
mid-cycle, that is a scope change and deserves an explicit conversation —
not a silent edit. That signal is what the format exists to give you.

---

## Conventions

**Etapa tags.** Prefix every activity with its ANP etapa — `[E1]`–`[E4]`.
Six weeks of slides can then be filtered by tag when a report is due,
instead of reconstructing the mapping from memory.

**Figures.** Use the project
[plot standard](../src/hpdac/utils/README.md), sized to 125 × 85 mm. The
same style that produces the report figures produces these, so nothing is
redrawn later.

**Files.** One deck per person, one slide per week, appended. The deck is
the archive — never overwrite last week's slide.

```
tracking/
├── One-Slide.pptx              # template, do not edit
├── cycle-02/
│   ├── lorenzoni.pptx
│   ├── faria.pptx
│   └── nakashima.pptx
```

---

## Discovery work

Six-week cycles come from product development, where the mechanism is fixed
time and variable scope. Research does not always descope: a rig either
commissions or it does not, a model either converges or it does not.

So separate two kinds of activity.

**Build work** — install, instrument, implement, integrate — takes a
deliverable and a date. This is most of E1 and E4.

**Discovery work** — *will this concept reach 120 °C at an acceptable COP?* —
takes a **decision point**, not a deliverable: *"Decide by w3 whether to
continue with approach A or fall back to B."* That converts an open-ended
risk into a scheduled choice, which is something a lead engineer can manage.
A discovery activity with a promised outcome is a promise nobody can keep.

---

## Failure modes

**Everything stays green.** Reporting an obstacle feels like admitting
failure, so people wait until it is undeniable — by which point the cycle is
over. Say once at kickoff and mean it: raising an obstacle is a request, not
a confession, and a cycle where none appeared probably had objectives that
were too easy.

**NEXT STEPS becomes a wish list.** Prevented only by reading last week's
lines aloud at the top of every meeting. Without that check, people learn
within a month that nothing follows from the block, and it fills with vague
verbs.

**The slide becomes a status report.** If the meeting is spent narrating
ACTIVITIES, the format has failed. Slides go out 24 hours ahead; the meeting
is for obstacles and decisions.

**Only the lead holds the integration picture.** 1:1 planning silos the
dependency map — and E2 is blocked on E1's data, E4 on E2's models. The
group session at kickoff exists to surface those before anyone commits.

**A step slips and disappears.** Carry it forward with its original date
visible: *"— A. Lorenzoni, 03/09, carried from 27/08"*. One slip is noise;
the same line carried three weeks running is a signal that the activity is
harder than estimated or blocked by something nobody has named.
