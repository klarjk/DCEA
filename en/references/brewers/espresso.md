# Espresso

Equipment-specific mechanisms. For variable directions see `variables.md`, for recipes see `recipes.md`.

**Premise**: the author cannot directly measure espresso flow rate (except on the Decent and the Belkafilter), so a large part of this area is **left at the theory stage**. Verification density is lower than on the filter side.

---

## The Three-Zone Preinfusion Model

The core of the author's theory. **"Preinfusion is tamping done with water."** (Source 11)

| Zone | State | Behavior under pressure |
|---|---|---|
| 1 Headspace | Empty space above the puck | Fills with water, pressure rises |
| 2 Wetted puck | Soaked with water | Water is not compressible, so it **only transmits force downward** |
| 3 Unwetted puck | Air between the particles | **Crushed downward, particle spacing narrows**; air is expelled out the bottom |

The boundary between 2 and 3 is the **infusing line**.

### Causal chain

```
Preinfusion flow rate ↑
 → headspace fills quickly (large pressure at an early point)
 → the infusing line at that point stays at a shallow position
 → the entire unwetted zone below it is compressed
 → the very bottom of the puck becomes a "very dense wall"
 → ① resistance ↑
   ② bottom flow-path cross-sectional area ↓ → flow velocity ↑ → crema ↑ · texture ↑
   ③ vertical uniformity ↓ → extraction yield ↓
```

With a low flow rate it is the reverse — infusing proceeds deep before the headspace fills, so there is little zone left to be compressed, the wall is thin, resistance is low, extraction yield is high and crema is scarce.

### Numbers

| Preinfusion flow rate | Result |
|---|---|
| **2~3ml/s** | Low resistance · thin wall · high extraction yield · little crema |
| **6ml/s** | High resistance · thick wall · low extraction yield · much crema (the author's previous setting) |
| **8ml/s** | The flow-rate target of Extractamundo Dos! |

- It takes **5~7 s or more** for the whole puck to be wetted. Even after that, flow does not start until pressure is above a certain level.
- When the water in the headspace presses down at 9bar, that force is **about 10× ordinary tamping**. But the author qualifies this — "pressure is applied while increasing gradually as well, so it is not really 10×".
- In Korea the Decent's maximum flow rate is **6ml/s** because of mains frequency.

### Extraction yield and crema are inversely related

| | Extraction yield | Crema |
|---|---|---|
| Thin wall · gentle PI · uniform particles | High | Little |
| Thick wall · fast PI · non-uniform particles | Low | Much |

> "Extraction yield and crema stand in an inverse relationship, so raising one requires sacrificing the other. **(Almost every element of coffee is like this.)**" (Source 11)

**The barista's role**: to know the tendencies of their own machine (water debit) and grinder (burr geometry, uniformity), and to allocate extraction yield and texture by adjusting the flow rate and pressure changes of the preinfusion.

### Preinfusion prescriptions by equipment (Source 11)

| Equipment condition | Recommended | Reason |
|---|---|---|
| water debit **8~10ml/s or more** (LM etc.) + a grinder with many fines and low uniformity (Nitsche Zero · Rover) | **Gentle** | Avoids the risk of under-extraction |
| water debit **6ml/s or less** + uniform EK-family burrs | **As abrupt and as short as possible** | Fills in the body that tends to be lacking, balancing flavor and sweetness (such equipment produces a high extraction yield anyway) |

### Flow rate · time · ramp rate are separate axes

- **High flow rate** → resistance↑ (Source 11)
- **Long time** → resistance↓, uniformity↑, crema↓ (Source 14, 16)
- **Gentle pressure ramp** → resistance can actually drop even when pressure is ramped earlier [Hypothesis] (Source 18, measurement section below)

**Do not lump the three axes together and assert that "reducing preinfusion raises resistance."** The measurements in Source 18 conflict with that assertion. Check which axis was moved, then answer.

**A preinfusion that is too long** weakens resistance and forces a finer grind size, and the resulting excessive extraction yield tastes sharp. The author's own practice is **5~10 s with a gentle pressure increase**, depending on days off roast. (Source 14)

---

## Preinfusion Measurements (Decent, Source 18)

If Source 11 is theory, this section is what the author actually measured from the Decent's resistance graph. Three profiles were compared.

### Success indicator — the flow-velocity gap

**The smaller the difference between the machine's flow velocity and the actual extracted flow velocity at the moment extraction begins, the more successful the preinfusion.** [Verified]

| Flow-velocity relation | State of the puck |
|---|---|
| Machine flow velocity = extraction flow velocity | The puck acts as a **conduit**. Stable |
| Machine flow velocity > extraction flow velocity | Pressure rises fast. The **top of the puck** is unstable |
| Extraction flow velocity > machine flow velocity | The compressed gas bursts out like an elastic body. The **bottom of the puck** is unstable |

This is a **different indicator** from Source 12's "interval between dwell time and the resistance peak." Source 12 looks at the length of the uneven-extraction segment; this indicator looks at which end the puck starts collapsing from. Decent users look at both together.

### Comparison of three profiles (at 6bar) [Verified]

| | Dwell time | Peak resistance | Flow-velocity gap at the start of extraction | Crema |
|---|---|---|---|---|
| Flat (no preinfusion) | 9 s | **Not measurable** (infinite — pressure is applied but flow velocity is 0) | Large | — |
| Low pressure 12 s (low pressure held until dwell time) | 12 s | Greatly lowered | Small | Little |
| Modified version (fill 2 s → wet 4 s → ramp pressure 6 s → hold) | 9 s | **Even lower than low pressure 12 s** | Widens again | Markedly more and longer-lasting |

**The reversal in the third one matters.** Peak resistance actually fell even though the pressure ramp was brought earlier. The author's interpretation is that ① pressure was ramped gradually, so the unwetted zone was not compressed much, and ② the puck was not fully wetted, so there were fewer particles for the water to pass through [Hypothesis]. That is, **ramp rate appears to govern resistance more than the absolute timing of the ramp** [Hypothesis] — a provisional conclusion drawn from a single comparison of three profiles.

With a low-pressure infusion, resistance peaks at dwell time and then falls as extraction begins — an **inverted-V curve**. [Theory]

### The price of a long low-pressure preinfusion

It buys early stability, but **resistance across the whole puck drops, so flow velocity in the late phase of extraction becomes very fast.** Then the extraction flow velocity exceeds the machine flow velocity late on, and **the bottom of the puck collapses, so channeling becomes frequent.** [Observed]

> "In practice channeling is frequent as the extraction nears its end."

Also, the long low-pressure segment means little crema — "if you are going to pull a shot with no crema, you may as well just extract it as a turbo shot".

**Three countermeasures for late-phase channeling** — on a Decent, try the flow limit first (since it only takes a settings change). Otherwise a paper filter is the default, and swapping the basket is considered only when the first two do not work.

| Method | Principle | Confidence |
|---|---|---|
| A **paper filter** at the bottom of the basket | Prevents particles from plugging the basket holes and then bursting through. Holes 300~500μm against paper of 20μm or less | [Observed] "I hardly ever saw spritzers (water jetting through the basket holes)" — recommended as the best value for money |
| **Limiting the machine's maximum flow rate** (the author uses 2.5ml/s) | Blocks the late-phase surge in brew speed itself. Decent only | [Observed] Stable, much like the paper filter |
| A basket with a large **open-area ratio** (Unifilter · WAFO) | Lowers the pressure borne by each hole | [Hypothesis] "I have only tried it a few times" |

### Dark roasts do not need preinfusion [Observed] (on the author's setup)

- At medium-dark roast and above, **coffee does not drip at all at low pressures of 2bar or less.** In most cases extraction starts only at 6~8bar or more
- The higher the roast level, the more strongly it is affected by **pressure** rather than by time
- A dark-roast puck is viscous and structurally stable — it acts as a conduit rather than an elastic body, and even without preinfusion the machine flow velocity and the extraction flow velocity are almost the same from start to finish

**If you still want to give it one**, use one of two criteria.
- The dwell time when pulled with a flat profile **+ 3 s** (because on a light roast the dwell-time difference between a hard pressure ramp and a low-pressure preinfusion is about 3 s)
- On a Decent, more precisely — the **midpoint between the dwell time and the peak-resistance point** of the flat profile

### Fill the headspace fast [Hypothesis]

The author chooses to fill the first 15ml or so at the fastest possible flow velocity. Water almost never falls evenly from the shower screen, so filling slowly spreads it around the spots where the droplets land and harms the puck's uniformity. But the author flatly stated **"this is only a guess, so it has no credibility"**, and ran no comparison experiment.

### Beginner's guide (Source 18, summarized)

1. The longer it is, the more stable the first half of the extraction [Verified]
2. But the longer it is, the less crema. **If you want a chewy espresso it is better not to do it** [Verified]
3. **5~6 s is the compromise point on the author's setup** [Observed] — shorter than that and the early phase is unstable, longer and crema is lost. Adjust within that range

### Shot timing — correct the brew time when there is preinfusion [Theory] (Source 18)

With preinfusion the total time can even exceed 40 s, so it becomes impossible to compare against a benchmark like "30~35 s for dark roast." The author converts it into **the time water was actually in contact with the coffee**.

```
corrected brew time = extraction end time − (dwell time ÷ 2)
e.g.) dwell time 6 s, end 38 s → 38 − 3 = 35 s
```

Rationale: until dwell time the water soaks in gradually from the top, so at the dwell-time point the top of the puck has been in contact with water for that whole time while the bottom has only just been touched. Averaged over the whole puck, contact amounts to **half the dwell time**.

Defined this way, the influence of time can be compared on the same ruler whether the preinfusion is long or short. **If the user is recording time this way, use that value as is.**

---

## Flow Velocity Inside the Puck (Bernoulli)

- Flow velocity is **inversely proportional to cross-sectional area**. The flow paths inside the puck are far narrower than the headspace (58mm diameter), so flow velocity inside the puck is faster, and **particle spacing narrows toward the bottom of the puck, where velocity is highest**. (Source 10)
- Where flow velocity is fast, pressure is low. Even when the headspace is at 9bar, **pressure inside the puck is far lower**. [Theory]
- This high flow velocity inside the puck is the key to crema formation. [Hypothesis]

---

## Crema Theory

**Crema = a meringue-type colloid** [Hypothesis] (Source 09)

The narrow gaps between particles act as a sieve, and the gas produced, the water, and the fat carried along by the water receive kinetic energy from the fast flow velocity, forming a colloid that holds fine bubbles.

Three conditions for it to hold: ① gas must be present ② a means of breaking that gas into fine pieces ③ water and fat must receive physical energy and mix around the gas.

### Crema variable directions

| Variable | Crema |
|---|---|
| Roast date · roast level | **The largest influence** (amount of gas produced) |
| Temperature ↑ | Increases |
| Brew speed ↑ | Increases (kinetic energy · fat increase) |
| Pressure ↑ | Increases |
| Finer grind size | Increases, then **decreases past a limit** (total flow rate no longer comes out) — non-monotonic |
| Brew ratio | **Maximum slightly toward lungo (around 1:2.2)**. Ristretto has a low flow rate so it is actually less, and beyond that pressure falls and it decreases — non-monotonic |
| Strong preinfusion | Increases |
| Narrow headspace | Increases |
| Narrow basket open area (IMS M) | Increases (lateral uniformity is sacrificed) |
| Fines proportion ↑ · large-particle uniformity ↓ | Increases |

**Crema color change during extraction**: right after the start, when speed is slowest, **dark black** → as speed builds, **the golden color deepens** → once the gas runs out, **it thins**.

**Grind size and color**: coarse gives a light color, fine a dark color (more fines are carried in).

### The author's view of crema

- The taste of crema itself is **harsh**. As roast levels come down, the unconditional pursuit of crema is losing ground.
- Even so, on a light roast **too little crema means a sharp flavor that is hollow in the middle**, so a reasonable amount is needed.
- **Tiger striping is not a good indicator** — fines have poor sensory notes and irritate the stomach.
- Prefers to extract plenty of crema but **halve the amount by splitting the shot with a two-spout**.

---

## Basket Geometry

**Center-concentrated perforation (IMS etc.)** → uniformity↓ · extraction yield↓ · **flavor↑**
**Even perforation (VST etc.)** → uniformity↑ · extraction yield↑ · flavor↓

Mechanism: when the diameter narrows toward the bottom, resistance grows, and during preinfusion the difference in particle spacing between top and bottom widens. The top gives up many coffee compounds and little flavor, the bottom the reverse, and it proceeds unevenly. Because espresso is high in concentration, it appears as **piercing, harsh acidity**. (Source 05)

**Correcting it with preinfusion can actually make it worse** — the deviation in particle spacing shrinks, but the structure that gathers flow inward stays the same, total flow rate rises further, and flavor extraction becomes excessive in a narrow zone, giving **a bitter aftertaste**.

### Total flow rate outranks geometry

The reason VST, with its smaller area difference, appears to extract flavor better than IMS, with its larger one, is **the difference in total flow rate**. IMS is used mostly with dark roasts and low flow rates (0.8~2ml/s or less), where the relative difference in flow velocity becomes meaningless.

> "You could say that in everyday use we are using the IMS basket not to bring out flavor but **to lower total flow rate through high resistance**." (Source 05)

**For light roasts the VST family is recommended.** High-yield baskets (Unifilter · WAFO) can be too much for a light roast — "extract at 1:2 and it is too sharp, grind coarser and you cannot hit 4bar, drop to 1:1 and the extraction yield still does not fall much, so it becomes an undrinkable beverage". That said, they may have strengths for diluted drinks.

---

## The Two-Sided Pressure Thresholds (Light Roast)

Based on the author's experience [Observed] (Source 14):

- **6bar or more** → flavor disappears and it tastes similar to a dark roast. Body is good but clarity drops
- **4bar or less** → almost no crema and the taste is sharp and uncomfortable to drink. "acidity like being stabbed with a knife"

Set the target at **6bar** and adjust the **grind size coarser** to land in the 4~6bar range.

The lower the pressure, the more even the extraction and the better the coffee compounds come across, but the extremes fail.

---

## Beans Suited to Light-Roast Espresso

Two factors decide it. (Source 14)

**① Intensity of the acidity** — a coffee whose balance leans toward acidity on the cupping table becomes too strong in taste when pulled as a high-concentration espresso. **Ethiopian washed and Geisha washed types with yellow and orange cup notes are difficult.**

**② Body** — body here is not a sense of concentration but **the nutty taste of fat**. The more of that fatty, soft, milk-like taste there is, the more it anchors the center of the palate and **acts as a buffer**, neutralizing sharp tastes.

Suitable beans: mostly **Central and South American types**, **natural** rather than washed, and large varietals like Pacamara and SL-28.

> "If on cupping you feel an abundance of soft, nutty fat, it goes straight to espresso. **Brewing this kind as filter actually kills the coffee's character.**"

---

## Quantitative Diagnosis of Uneven Extraction (for Decent Users)

Read it off the resistance graph. (Source 12)

- Look at the interval between **dwell time** (the point water arrives) and **the point resistance peaks**
- The peak-resistance point = when the puck is wetted to the maximum at that pressure
- The segment between them is **the time extraction proceeded unevenly**, and it affects the shot through to the late phase
- The author's case: dwell time 6 s, resistance peak 9.5 s → **3.5 s of uneven segment**

The mitigations are **a soft preinfusion and blooming**, but overdoing it backfires badly depending on the equipment.

---

## Beans That Have Lost Their Gas

When too long has passed since roasting, all the gas has escaped, so **no resistance builds and extraction becomes difficult.** [Verified]

Compensations: updosing, nutation tamping, a rotary distributor, swapping the basket. But "you can compensate with tricks, though quality drops".

---

## Other Practices

- **A paper filter at the bottom of the basket** (Kalita round filter 53mm etc.) — prevents spritzers + slightly improves clarity. The author recommends it strongly. For the principle of spritzer prevention and other countermeasures see "Three countermeasures for late-phase channeling" above
- **Puck screen** — used to reduce the amount of coffee while maintaining the headspace. **It encourages edge-biased extraction, so use it only together with a maximum-flow-rate preinfusion**
- **The larger the basket size and dose, the higher the extraction yield** — when the puck is tall the coffee particles themselves act as a filter, lowering the chance that fines plug the bottom and the holes [Hypothesis]
- **Robusta blending** — high in fat, so the crema proportion is very high. A lever-machine-family profile that lowers pressure and flow rate in the late phase suits it
