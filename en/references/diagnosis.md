# Sensory Diagnosis Table

Sensory input → cause → prescription. Source citations and confidence tags are the same as in `model.md`.

---

## The Brew Speed Spectrum

Place the user's sensory notes on this ruler to estimate where the average flow rate sits. (Source 16)

```
(fast) ──────────────────────────────────────────────── (slow)
dry,          greenish,        good        sweet      sweet and dark,
astringent    dried fruit      flavor                 tone-downed, dull
```

**Astringency sits at the fast end.** This is the opposite of conventional wisdom (astringency = over-extraction). In the author's model astringency arises not from "extracting too much" but from **water continuing to pass through even after the extractable F has run out**. [Hypothesis] (Source 01)

---

## Astringency and Greenness Are Diagnosed Separately

Both look like "too fast", but the manipulation target differs. Lump them together and the wrong prescription goes out.

| | Astringency | Greenness (greenish) |
|---|---|---|
| Cause | the **peak instantaneous value** of flow velocity is high | the **average flow rate** (flow rate × time) is large |
| Prescription | put a **cap** on the early flow rate | lower the concentration, or lower the flow velocity **across the whole run** |

---

## Diagnosis and Prescription by Negative Sensory Note

### Astringency · dry
- **Cause**: excessive absolute flow velocity / very high concentration / the coffee bed cannot support the flow (insufficient dose) / insufficient fines (a grinder with high unimodality) [Theory+Verified] (Source 07, 06)
- **Prescription**: put a cap on the peak early flow rate. In the author's experiment, **lowering it to 4mlps or below made astringency entirely imperceptible**. (Source 06)
- **Exception prescription**: if the drying sensation continues even when none of the conditions above apply → **raise the brew ratio (pour less water) and open up the grind size to hold the concentration**. On the author's equipment (P64 SSP LS): medium-light at 1:16 is slightly astringent and **at 1:15 there is almost none**; light and Nordic are fine up to 1:17. **This limit line differs from grinder to grinder.** [Observed] (Source 01)

### Piercing sourness
- **Cause**: fast flow velocity + short time + small beverage weight + high concentration (Source 07)
- **Prescription**: ① increase the beverage weight to lower the concentration and secure more sweetness compounds ② or slow the flow velocity

### Greenness (greenish · dark green)
- **Cause**: flow rate × time is large + high concentration. **This is not under-extraction but over-extraction of flavor.** (Source 07)
  > "Greenness has long been known as a sensory note of under-extraction, because raising the brew ratio to increase the yield solved it; but I think it is actually over-extraction of flavor."
- **Prescription**: ① the easiest way — increase the beverage weight or reduce the dose to **lower the concentration** ② to avoid it while holding TDS, lower the flow velocity across the whole run to increase the immersion proportion ③ **lower the temperature by 3°C**
- **Dripper caution**: it appears with high probability when you raise the concentration on a dripper like the V60, which has a fast flow velocity and holds that flow velocity well. (Source 07) The lower part of the V60 is deep, so gas has trouble dispersing and the greenness stays in the cup [Hypothesis] — give it a center-concentrated blooming, or dig the center out into a bird's-nest shape. (Source 13)
- **Which side it belongs to**: greenness is **on the F (light flavor compounds) side.** The "relatively heavy vegetal flavor" in Source 07 refers to the ordering — that it comes out later than sour · citrus within F — not to a classification as C. Prescribe on the F basis — **it is over-extraction, so the direction is to reduce**.

### Mucus-like texture (viscous)
- **Cause**: over-extraction of the greenness compounds + extremely high concentration (Source 07)
- **Prescription**: same direction as greenness

### Fermented off-note (fermented)
- **Cause**: the faster the flow velocity, the worse it gets. (Source 07)
- **Prescription**: ① **prevention through frozen airtight storage** is best ② if unavoidable, lower the flow velocity and extract slowly (give up the bright acidity and flavor)

### Bitterness
- **Cause**: "a sensory note of chaos" — a state where both the flavor and the heavy compounds are excessive. "the way a herbal decoction boiled from many different medicinal ingredients tastes bitter" [Hypothesis] (Source 07)
- **Prescription**: no single prescription. Treat it as a signal of balance collapse and probe further for other clues.

### Flatness · barley tea · grainy · hollow in the middle
- **Cause**: FCR < 1. The total flavor load is insufficient. (Source 01, 03)
- **Prescription**: **Lower the flow rate and raise the TDS.** Increase the number of pours, and increase the dose.
- **Caution**: raising the flow rate here is the forbidden path in `model.md`.

### The first sip is hot and uncomfortable + greenness (gone once it cools)
- **Cause**: excessive temperature makes the flavor expression excessive. (Source 06)
- **Prescription**: **Hold all other variables fixed and lower only the temperature by 3°C.** The author has a measurement in which this manipulation alone removed the greenness. [Verified]

### Different coffees taste the same
- if floral · sweet · berry appear regardless of the bean, it is a defect. See "The Definition of an Extraction Defect" in `model.md`.

---

## Diagnosis by Separating Smell and Taste (Source 13)

Split whether the negative impression is a taste (concentration) problem or a smell (flavor stimulus) problem.

```
negative taste
  ├─ concentration is not excessive  AND  there was no uneven extraction or mistake
  │     → confirmed as a smell problem → correct with degassing and temperature
  └─ otherwise → an extraction problem → correct with flow rate, grind size, brew ratio
```

The author's original gate takes **TDS 1.5% or below** as the criterion. Without a refractometer, judge whether the concentration is excessive from the brew ratio and the time.

> "If the number the refractometer shows is not too high (1.5% or below), and if there was also no mistake in a particular part of the brewing process and no sign of uneven extraction, I think the negative stimulus can be reduced through exactly this degassing and temperature control, and in practice it is effective." [Verified]

**The key reinterpretation**: the author sees **most** of the bitter, astringent, harsh sensations commonly known as over-extraction **as excessive olfactory stimulus**. Greenness · greenish is likewise an excess of a particular flavor. [Hypothesis] (Source 13)

---

## Degassing · Temperature Control

- Temperature upper limit **100°C**, lower limit **the mid-80s °C** (go below that and the temperature drops too much while drinking). (Source 13)
- Temperature by days off roast (on the author's espresso setup): **5~10 days 86°C / 10 days~3 weeks 90°C / after 3 weeks 93°C or above**. [Observed] (Source 14)
- **The criterion is not the date but the comparison with yesterday** — "if the coffee drunk today is clearly weaker in flavor than yesterday's, raise the temperature by 3~4°C". (Source 14)
- If insufficient degassing gives greenness → **resting after grinding**. The author saw an effect from leaving it only **30 minutes** after grinding. [Verified] (Source 13)
- For Nordic, Loring-roasted, and hard beans that do not crush when pressed, the baseline degassing is **2 weeks or more**. (Source 13)
- If the greenness takes **3 weeks to a month or more** to disappear, judge it a bad roast. The same goes for the case where the good aroma disappears along with the greenness and it turns flat. (Source 13)

---

## Rules to Follow When Diagnosing

- **Change only one variable at a time.** Change several at once and next time you cannot tell which one had the effect.
- **If information is lacking, probe further.** Do not invent plausible-sounding advice while it is still lacking.
- **After prescribing, tell the user what to check.** State explicitly which sensory note must change in what way in the next cup for it to count as success.
