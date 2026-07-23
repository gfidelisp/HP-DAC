# One-Slide Follow-Up

Project tracking for Hp-DAC. One slide per objective per week — objective,
activities, obstacles, results, next steps.

| File | Use |
|---|---|
| `One-Slide.pptx`, slide 1 | Template with guidance and worked examples — read once |
| `One-Slide.pptx`, slide 2 | Blank working slide — duplicate this one every week |

---

## The cycle

Work runs in **six-week macro cycles**.

| Phase | What happens |
|---|---|
| **Kickoff** (day 1) | Sessions with each developer to set the cycle objective and activity list |
| **Weeks 1–6** | Weekly meeting, one slide per developer |
| **Close** (week 6) | Review against the objective: what landed, what didn't, why |

**Weekly meeting.** Slides circulate ahead so nobody reads status
aloud. 
---

## Filling the slide

### Header — `1. FOLLOW-UP - OWNER`, `DD/MM/AAAA - DD/MM/AAAA`

Sequential number, owner's name, and the week's date range. The number runs
across the whole project so the deck accumulates into an archive:

### OBJECTIVE — *what this cycle is for*

**Written at kickoff, unchanged for all six weekly slides.** 

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
Decide, Document*. 

A verb forces a completion condition. Avoid *Study, Analyse, Investigate,
Work on, Improve, Explore*. They have no end state and will run the whole
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

Each line carries the obstacle, its effect on the objective, who removes it,
and by when. The owner is whoever *can* remove it.

> Manufacturer data covers only 35–75 °C condensing, leaving the 85–120 °C
> range needed for DAC unsupported by any fit.

When there is nothing, write **None**. A blank box reads as an unfilled
field, not as a clear week.

### RESULTS — *what do we now know that we didn't last week*

The largest block on the slide: **Figures Tables, and Sentences
saying what they shows.** Evidence, not activity. Data, not narrative.

The sentence states what the evidence *means*, with a number — same
discipline as a figure caption.

> COP falls from 3.4 to 2.1 as the sink temperature rises from 60 to 95 °C;
> the model overpredicts by 8% above 85 °C.

A negative result is a result. A week with no new evidence says so in one
line and leaves the previous figure in place.

### NEXT STEPS — *what will be true at the next meeting*

The coming week only — the rest of the cycle lives in ACTIVITIES. Every line
traceable to an activity, verb-first.

Filled in **two passes**. Before the meeting, the owner drafts their proposed
steps; that version circulates. During the meeting, team feedback is added to
the same block, and the post-meeting version is the record. Save it over.

> **Drafted before**
> Repeat the 90 °C test with the recalibrated Coriolis meter.
>
> **Added in the meeting**
> Check the suction-line insulation before rerunning; it may explain the 8%
> overprediction.

---
