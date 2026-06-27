---
name: dsa-coding-patterns-study-guide
description: >-
  Generate polished, ORIGINAL HTML study guides for coding-interview / DSA
  preparation, organized as reusable PATTERNS (Two Pointers, Sliding Window,
  Fast & Slow Pointers, Binary Search, BFS/DFS, Backtracking, Heaps, Intervals,
  Monotonic Stack, Dynamic Programming, Union-Find, Tries, Prefix Sums, etc.),
  with clean schematic data-structure diagrams (array cells with index labels,
  labeled pointer carets, linked-list nodes with next-arrows and cycle
  loop-backs, trees, and grids) rendered as inline SVG, a consistent design
  system, interactive step-through visualizers, trade-off tables, a graded
  practice ladder, and a self-test. Use this skill whenever the user wants to
  study, learn, review, revise, drill, or create study material for data
  structures & algorithms or coding-interview patterns, prepare for a
  software-engineering / LeetCode-style live-coding interview, or asks to
  visualize how an algorithm or data structure works in a clean, textbook-style
  diagram — even if they never say the words "study guide." This is the sibling
  of the system-design-study-guide skill and shares its exact design system.
---

# DSA / Coding-Patterns Interview Study Guide Generator

Produce a single self-contained HTML lesson that teaches one **coding-interview
pattern** deeply and is pleasant to study from, replay, and quiz yourself
against. The output looks like a refined technical textbook chapter: a sticky
table of contents, a scroll progress bar, prose explanations, clean schematic
SVG diagrams of arrays / lists / trees with pointers in motion, trade-off
tables, interview-tip callouts, a graded practice ladder, and an end-of-lesson
self-test.

The audience is someone preparing for a coding interview (e.g. live-coding
rounds at large tech companies, or at regional employers — in Singapore that
means Grab, Sea/Shopee, GovTech, ByteDance/TikTok, the big-tech offices, and the
banks). Optimize relentlessly for that: every technique is tied to the
**bottleneck it removes** (a brute force that is too slow or too memory-hungry),
reinforced with the kind of follow-up questions an interviewer actually asks,
and backed by problems the reader can immediately drill.

---

## Read first: three non-negotiables

**1 — Content must be original.** Never reproduce text, wording, structure,
diagrams, or problem statements from any paid course (ByteByteGo, NeetCode,
AlgoExpert, Grokking, etc.), book, or copyrighted source — not even reworded
sentence-by-sentence. These patterns are standard computer-science fundamentals
taught in countless free places; explain them in your own words, with your own
examples, arrays, and framing. You **may name well-known problems** ("Two Sum
II", "Sort Colors", LeetCode numbers) as short factual identifiers, but **write
every problem description yourself** — never paste or closely paraphrase the
original prompt. If a user links or uploads material from a paid product, treat
it only as a reference for *which pattern to cover* and the *visual style* —
study the look, then write and draw everything fresh.

**2 — Drive the narrative with the bottleneck.** The strongest interview answers
are a chain of cause and effect: *the naive solution is O(n²) / needs O(n)
space, so we do this instead.* Open every section with the brute force and its
complexity, then introduce the insight that removes the redundant work, then
state the **invariant** that makes it correct. A reader who internalizes the
"why it's slow → the trick → the invariant" chain can reconstruct the algorithm
from first principles on a whiteboard.

**3 — Be practice- and interview-focused.** Favor recognition cues, trade-offs,
edge cases, and "why" questions over exhaustive theory. **Every technique
section carries one fully worked, named LeetCode problem** — an original prompt,
a linear reasoning chain from brute force to the trick, the actual code, and a
script for narrating it to the interviewer — so the reader sees the pattern go
from idea to a real, codeable solution they can defend out loud. **Every lesson
ends with a graded practice ladder** of real problems (described originally)
**and a self-test.** End each major concept by gesturing at what an interviewer
would probe next.

---

## Output format

- Produce **one self-contained `.html` file** (all CSS and JS inline; fonts via
  Google Fonts `<link>`). No external JS dependencies, no build step.
- **Never use `localStorage`, `sessionStorage`, or any browser storage** — it
  breaks in sandboxed renderers. Keep all state in memory.
- Save to the outputs directory and present it. Name it descriptively, e.g.
  `lesson-02-sliding-window.html`.
- If the user wants several lessons, also offer a small `index.html` that links
  them into a course.

---

## Lesson structure

Use this skeleton for every lesson. Adapt the number of sections to the pattern.

```
1. Header / hero
   - lesson/pattern number badge + "Pattern · Coding Interview" eyebrow
   - <h1> pattern title
   - .lede one-paragraph framing of the family of problems it solves
   - .disclaimer note: original study material; problem names are identifiers
     only; mention the N interactive diagrams
2. Numbered sections (the body)
   - Each section = one variant / insight that removes ONE complexity bottleneck,
     in escalating order.
   - Section anatomy (in order):
       a. .steptag  ->  "<b>NN</b> short phase label"
       b. <h2>      ->  the variant / step name
       c. prose     ->  brute force + its big-O, THEN the insight, THEN the
                        invariant + final complexity (time AND space)
       d. <figure>  ->  a schematic SVG (static) or an interactive stepper, + "FIG. N" caption
       e. optional .vs trade-off table (e.g. two pointers vs hash map)
       f. optional .callout (blue = "the reusable shape" / why it works)
       g. REQUIRED .worked  ->  one fully worked, NAMED LeetCode problem for THIS
                        technique (see "Worked problem walkthrough" below): an
                        original prompt, a "think it through" reasoning chain
                        (restate -> brute force + big-O -> the waste -> the move
                        -> invariant + cost), the actual CODE, and a script for
                        narrating it to the interviewer + the edge cases to
                        dry-run. Every technique section gets exactly one.
       h. optional .callout.tip (rust = "what the interviewer asks next")
3. Practice ladder (REQUIRED)
   - a #s? section with a .ladder of .drill cards, grouped Easy -> Medium -> Hard.
   - Each .drill: difficulty .pill, problem .nm, a variant .tag, an ORIGINAL
     one-line prompt, and an .idea line ("Idea: the move + target complexity").
   - End with a .callout.tip on HOW to drill (narrate, state big-O, dry-run edges).
4. Summary & self-test
   - .takeaways grid of principle cards
   - a .callout.tip self-test: 5-6 "cover the notes and answer aloud" questions
     targeting the invariant + when-to-use of each variant.
```

Writing voice: clear, concrete, second-person where natural. Define a term the
first time it appears in **bold** (e.g. **invariant**, **monotonic**). Prefer
short paragraphs. Use `<code>` for variables, operators, and complexities
(`slow`, `a[L]`, `L < R`, `O(n log n)`). Keep bullet lists scannable.

### Concept lessons (a lighter variant)

A few entries on the course map (marked **◇**) are **concepts or data-structure
primers**, not patterns: the framework lesson (L00), complexity analysis (L01),
and the standalone structure refreshers (L02–L08: arrays, hash maps, linked
lists, stacks/queues, trees, heaps, graph representations). These have no single
"brute force → trick → invariant" chain, so they relax the template:

- Keep the header, numbered sections, diagrams, trade-off tables, callouts,
  summary cards, and self-test exactly as usual.
- Replace the **required worked-problem block** with whatever fits the concept:
  for L00, a step-by-step walkthrough of the method on one example problem; for
  L01, a "read the target Big-O off the input size" table plus a few before/after
  complexity analyses; for a structure primer, the core operations with their
  costs and one short "see it used" snippet.
- The **practice ladder** becomes a "where this shows up next" pointer to the
  pattern lessons that build on it (e.g. the heaps primer L07 → Top-K & Two
  Heaps L28; graph representations L08 → graph traversal L23) rather than a
  graded drill set — unless graded drills genuinely fit.

Everything else — the design system, diagram conventions, the stepper engine,
and the self-test — is identical, so a concept lesson still feels like the same
course. Pattern lessons (everything not marked ◇) keep the full template, worked
problem and graded ladder included.

---

## Diagram style guide (the signature visual)

Diagrams are the heart of this skill. For DSA they depict **data structures with
pointers**, not system architecture. They must read like clean, hand-tidied
textbook figures: a few labeled cells/nodes, clearly colored pointers, a short
caption. Draw them as **inline SVG**, full width (`width:100%;height:auto`),
wrapped in `<figure><div class="blueprint">…</div><figcaption>FIG. N — …</figcaption></figure>`.

### Visual vocabulary

- **Array** → a row of rounded-rect **cells** (`.cell`), value centered inside
  (`.cellv`), zero-based index below in small mono (`.celli`).
- **Pointer** → a small triangular **caret** that sits at a cell with a short
  label (`L`/`R`, `slow`/`fast`, `i`/`j`, `low`/`mid`/`high`). Place opposing
  pointers on opposite sides of the row (one above, one below) so they never
  collide when they meet. A pointer is a `<g class="ptrmark …">` you reposition
  with a `translate(cellCenterX, baselineY)` transform per step.
- **Cell state** → recolor cells to show the algorithm: `.lo` (blueprint blue =
  left/slow/i pointer cell), `.hi` (amber = right/fast/j pointer cell), `.ok`
  (green = kept / matched / settled), `.faint` (dim = discarded / leftover).
- **Linked list** → **nodes** as circles (`.llnode`) with letter/value labels,
  joined by straight `.flow` next-arrows; a **cycle** is a curved `.flow-r`
  loop-back arc from the tail to the entry node; `.llnode.meet` (green) marks a
  meeting node.
- **Tree / grid** → reuse `.llnode` circles + `.flow` edges for trees; reuse a
  lattice of `.cell` rects for matrices/grids. Keep ≤ ~7 elements visible per
  figure; if it needs more, split it.
- **Caption**: centered, small monospace, `FIG. N — short description`. Always
  add a meaningful `aria-label`.

### Color coding (keep consistent across every lesson)

| Role                                   | Accent                  |
|----------------------------------------|-------------------------|
| Pointer A · left · slow · `i`          | blueprint blue `#1F4E79`|
| Pointer B · right · fast · `j`         | amber `#C98A2B`         |
| Kept · matched · valid · settled       | green `#69B34C`         |
| Discarded · out-of-window · leftover   | dim / faint gray        |
| Secondary structure · target · hash    | violet `#6E59A5`        |
| Visited / scanned region               | faint sand              |

### Diagram quality bar

- One idea per diagram. Lead the reader to redraw it from memory on a whiteboard
  (tell them to).
- Prefer an **interactive stepper** when the figure shows a *sequence* — a
  pointer sweep, a write index filling, a window growing/shrinking, tortoise &
  hare advancing, a BFS frontier expanding. Keep **comparisons/structure**
  static (brute-force-vs-pattern, region partitions, trade-off illustrations);
  animating those adds noise, not insight. Aim for ~3 interactive figures per
  lesson.

---

## Interactive (animated) diagrams

Wrap the figure's `div.blueprint` with an extra `stepper` class and a unique
`id`. Include a hidden `<circle class="packet" r="7" style="display:none"/>`
(the engine expects it). Below the SVG add the caption row and control bar
(Restart / Prev / Play / Pause / Next). For pointer-based DSA figures, **drive
all motion through the `onStep(idx, step)` callback** — reposition pointer `<g>`s
and recolor cells/nodes — and pass steps that carry only `text` (do not add
`.st` classes, so the engine's dim logic stays out of the way and the packet
stays hidden). Mark interactive lessons with a "▸" hint in the TOC.

```html
<figure>
  <div class="blueprint stepper" id="fig-conv">
    <svg viewBox="0 0 640 200" role="img" aria-label="Interactive converging two-pointer search">
      <g id="c-cells"></g>                <!-- buildRow() fills this -->
      <g id="c-L" class="ptrmark lo"><path d="M0,2 L-7,16 L7,16 Z"/><text y="30" text-anchor="middle">L</text></g>
      <g id="c-R" class="ptrmark hi"><path d="M0,2 L-7,16 L7,16 Z"/><text y="30" text-anchor="middle">R</text></g>
      <text id="c-read" class="readout" x="320" y="186" text-anchor="middle"></text>
      <circle class="packet" r="7" style="display:none"/>
    </svg>
    <div class="stepcap"><span class="stepnum">Step 1 / 6</span><span class="steptext"></span></div>
    <div class="controls">
      <button data-act="restart" title="Restart">&#8635;</button>
      <button data-act="prev">&#9664; Prev</button>
      <button data-act="play">&#9654; Play</button>
      <button data-act="next">Next &#9654;</button>
    </div>
  </div>
  <figcaption>FIG. 1 — interactive: each comparison throws away one end</figcaption>
</figure>
```

### Engine (paste once; powers every stepper — IDENTICAL to the system-design skill)

```js
function makeStepper(root, steps, onStep){
  if(!root) return;
  var svg=root.querySelector('svg'), packet=svg.querySelector('.packet');
  var numEl=root.querySelector('.stepnum'), txtEl=root.querySelector('.steptext');
  var btnPlay=root.querySelector('[data-act="play"]');
  var stage=Array.prototype.slice.call(svg.querySelectorAll('.st'));
  var i=0, playing=false, raf=null, timer=null;
  function pointAt(p,t){var L=p.getTotalLength(),q=p.getPointAtLength(L*t);
    packet.setAttribute('cx',q.x);packet.setAttribute('cy',q.y);}
  function animate(p){cancelAnimationFrame(raf);var dur=850,start=null;
    function f(ts){if(start===null)start=ts;var t=Math.min((ts-start)/dur,1);
      pointAt(p,t);if(t<1)raf=requestAnimationFrame(f);}raf=requestAnimationFrame(f);}
  function show(idx,doAnim){
    i=idx;var s=steps[idx];
    numEl.textContent='Step '+(idx+1)+' / '+steps.length; txtEl.textContent=s.text;
    var act=s.active||[];
    stage.forEach(function(el){el.classList.toggle('dim',act.length>0 && act.indexOf(el.id)===-1);});
    if(onStep)onStep(idx,s);
    if(s.path){var p=svg.querySelector('#'+s.path);
      if(p){packet.style.display='';packet.setAttribute('fill',s.reject?'var(--rust)':'var(--blueprint)');
        if(doAnim)animate(p);else pointAt(p,1);}
    }else{packet.style.display='none';}
  }
  function stop(){playing=false;btnPlay.innerHTML='&#9654; Play';clearInterval(timer);cancelAnimationFrame(raf);}
  function play(){if(playing){stop();return;}
    playing=true;btnPlay.innerHTML='&#10073;&#10073; Pause';
    if(i>=steps.length-1)show(0,true);else show(i,true);
    timer=setInterval(function(){if(i>=steps.length-1){stop();return;}show(i+1,true);},1900);}
  root.querySelector('[data-act="next"]').onclick=function(){stop();show(Math.min(i+1,steps.length-1),true);};
  root.querySelector('[data-act="prev"]').onclick=function(){stop();show(Math.max(i-1,0),false);};
  root.querySelector('[data-act="restart"]').onclick=function(){stop();show(0,false);};
  btnPlay.onclick=play; show(0,false);
}
```

### DSA building blocks (paste once; build & update array rows and move pointers)

```js
function _el(id){return document.getElementById(id);}
function _attr(id,k,v){var e=_el(id);if(e)e.setAttribute(k,v);}
function _mv(id,x,y){_attr(id,'transform','translate('+x+','+y+')');} // move a pointer <g>

// Build a row of array cells into <g id="PREFIX-cells">. Returns x-centers.
// The prefix is taken from the <g> id, e.g. "c-cells" -> ids c-c0/c-v0, "r-cells" -> r-c0/r-v0.
function buildRow(gid, values, baseX, topY, w, h, pitch){
  var g=_el(gid); if(!g) return [];
  var centers=[], prefix=gid.split('-')[0], NS='http://www.w3.org/2000/svg';
  for(var k=0;k<values.length;k++){
    var x=baseX+k*pitch, cx=x+w/2; centers.push(cx);
    var r=document.createElementNS(NS,'rect');
    r.setAttribute('class','cell'); r.setAttribute('id',prefix+'-c'+k);
    r.setAttribute('x',x); r.setAttribute('y',topY); r.setAttribute('width',w); r.setAttribute('height',h); r.setAttribute('rx',6);
    g.appendChild(r);
    var tv=document.createElementNS(NS,'text');
    tv.setAttribute('class','cellv'); tv.setAttribute('id',prefix+'-v'+k);
    tv.setAttribute('x',cx); tv.setAttribute('y',topY+h/2+6); tv.setAttribute('text-anchor','middle');
    tv.textContent=values[k]; g.appendChild(tv);
    var ti=document.createElementNS(NS,'text');
    ti.setAttribute('class','celli'); ti.setAttribute('x',cx); ti.setAttribute('y',topY+h+15); ti.setAttribute('text-anchor','middle');
    ti.textContent=k; g.appendChild(ti);
  }
  return centers;
}
// Re-apply per-step classes (and optionally values) to every cell.
function setCells(prefix, n, classer, valuer){
  for(var k=0;k<n;k++){
    var r=_el(prefix+'-c'+k); if(r) r.setAttribute('class','cell'+(classer(k)?' '+classer(k):''));
    if(valuer){var t=_el(prefix+'-v'+k); if(t) t.textContent=valuer(k);}
  }
}
```

Typical use (converging two-pointer): `var C=buildRow('c-cells', A, 134,70,48,44,54);`
then inside `makeStepper(_el('fig-conv'), steps, function(idx,s){ setCells('c',
A.length, k=>(s.done&&(k===s.l||k===s.r))?'ok':''); _mv('c-L',C[s.l],116);
_mv('c-R',C[s.r],116); _el('c-read').textContent=…; });`. For **in-place**
figures (dedupe, move-zeroes) give every step a full `vals` snapshot and have
`valuer` read `s.vals[k]`, so values mutate faithfully and reset on Prev/Restart.
For **linked lists**, create `circle.llnode` + letter `text` per node, straight
`path.flow` edges, one curved `path.flow-r` loop-back for a cycle, and move
`slow`/`fast` carets with `_mv` (place `slow` above the nodes, `fast` below).

---

## Worked problem walkthrough (one per technique — REQUIRED)

Every technique section must end with **one `.worked` block**: a single, named,
real LeetCode problem taken end-to-end. This is where the abstract pattern
becomes a concrete, codeable, *defendable* solution. The figure shows the
mechanism move; the worked block shows the reader how to **think**, **code**,
and **talk** their way through an actual problem that uses it. Pick a problem
that the section's figure already illustrates (or a near sibling of it) so
concept → visual → full solution reinforce each other.

**Originality still binds (non-negotiable #1).** Name the problem and its
LeetCode number as a bare identifier ("Two Sum II", LeetCode 167); then **write
the prompt, the reasoning, the code, and the narration entirely yourself.**
Never paste or closely paraphrase the official statement. Verify the code is
correct before shipping (mentally dry-run it, including the edge cases you tell
the reader to dry-run).

A `.worked` block has, in order:

1. **`.whead`** — the eyebrow "Worked problem", a difficulty `.pill` (`e`/`m`/`h`),
   and a `.lc` LeetCode-number chip pushed right.
2. **`.wname`** — the problem name (as an identifier).
3. **`.wprompt`** — the problem in *your own words*, 1–2 sentences. Bold the hard
   constraint (e.g. **in place**, **O(1) space**, **1-based**).
4. **`.wh` "Think it through"** then a **`.wsteps`** list of labeled `.ws` stages —
   the linear reasoning chain, one named stage each: **Restate → Brute force**
   (with its big-O in `<b>`) **→ The waste** (what the brute force ignores) **→
   The move** (the pointer rule; split into phases for multi-phase algorithms
   like Floyd) **→ Invariant & cost** (the one-sentence invariant + final time
   AND space in `<b>`). This *is* the "how to think about it linearly" the
   reader needs; keep each stage to a sentence or two.
5. **`.wh` "The code"**, a `.codetag` language label, then a **`pre.code`** block
   with the real solution. Default to **Python** (cleanest to read); the pattern
   translates. Lightly syntax-highlight with the `pre.code` token spans
   (`.kw` keywords, `.fn` the def name, `.cm` comments, `.lit` numbers/None).
   Escape `<`, `>`, `&` as entities. Keep it short — the five-to-fifteen lines
   that are the actual answer, well commented.
6. **`.say` "Narrate it to the interviewer"** — an *italic, first-person script*
   (in quotes) that walks the panel through the solution in the same order:
   restate → brute force + big-O → "but I'll use …" → the move → the invariant →
   the complexity. Close with a `.say .plain` line naming the **edge cases to
   dry-run aloud** (empty input, single element, all-equal, self-loop, etc.).
   This is the "how to explain it to the interviewer" deliverable — the script
   should be sayable verbatim in a live round.

The CSS classes (`.worked`, `.whead`, `.wk`, `.lc`, `.wbody`, `.wname`,
`.wprompt`, `.wh`, `.wsteps`, `.ws`, `.wsk`, `.codetag`, `pre.code` + token
spans, `.say`) are in the design-system block below.

```html
<div class="worked">
  <div class="whead"><span class="wk">Worked problem</span><span class="pill e">Easy</span><span class="lc">LeetCode 167</span></div>
  <div class="wbody">
    <div class="wname">Two Sum II — Input Array Is Sorted</div>
    <p class="wprompt">Sorted array + a target; return the <strong>1-based</strong> indices of the pair that sums to it. (Original wording.)</p>
    <h4 class="wh">Think it through</h4>
    <div class="wsteps">
      <div class="ws"><span class="wsk">Restate</span><p>…</p></div>
      <div class="ws"><span class="wsk">Brute force</span><p>All pairs, <b>O(n²)</b>.</p></div>
      <div class="ws"><span class="wsk">The waste</span><p>Ignores that it's sorted.</p></div>
      <div class="ws"><span class="wsk">The move</span><p>L/R inward; grow or shrink the sum.</p></div>
      <div class="ws"><span class="wsk">Invariant &amp; cost</span><p>Answer stays in [L,R]; <b>O(n) time, O(1) space</b>.</p></div>
    </div>
    <h4 class="wh">The code</h4>
    <p class="codetag">python</p>
    <pre class="code"><code><span class="kw">def</span> <span class="fn">twoSum</span>(numbers, target):
    L, R = <span class="lit">0</span>, len(numbers) - <span class="lit">1</span>
    <span class="kw">while</span> L &lt; R:
        s = numbers[L] + numbers[R]
        <span class="kw">if</span> s == target: <span class="kw">return</span> [L+<span class="lit">1</span>, R+<span class="lit">1</span>]   <span class="cm"># 1-based</span>
        L += <span class="lit">1</span> <span class="kw">if</span> s &lt; target <span class="kw">else</span> <span class="lit">0</span>      <span class="cm"># (illustrative)</span>
        ...</code></pre>
    <div class="say">
      <span class="k">Narrate it to the interviewer</span>
      <p>"Restating it … the brute force is O(n²) … but I'll use two pointers … my invariant is … that's O(n) time, O(1) space."</p>
      <p class="plain">Dry-run aloud: a two-element array; the <code>L &lt; R</code> guard.</p>
    </div>
  </div>
</div>
```

---

## Design system (CSS)

Drop this in a `<style>` block. It is the **same cream/blueprint "technical
paper" system as the system-design-study-guide skill** (so both courses look
like one product), plus DSA-specific cell/pointer/ladder classes at the end.
Keep the structure; tune nothing unless asked.

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600;9..144,700;9..144,900&family=Newsreader:opsz,wght@6..72,400;6..72,500;6..72,600&family=JetBrains+Mono:wght@400;500;600&display=swap');
:root{
  --paper:#F7F3EB; --paper-2:#FDFBF6; --ink:#20201D; --ink-soft:#5A574E;
  --blueprint:#1F4E79; --blueprint-soft:#4A7BA6; --blueprint-wash:#E9EFF5;
  --rust:#B0532F; --rust-wash:#F6E7DE; --line:#E3DBCB; --line-strong:#D2C7B0;
  --amber:#C98A2B; --green:#69B34C; --violet:#6E59A5; --maxw:780px;
}
*{box-sizing:border-box} html{scroll-behavior:smooth}
body{margin:0;background:var(--paper);color:var(--ink);
  font-family:"Newsreader",Georgia,serif;font-size:19px;line-height:1.65}
body::before{content:"";position:fixed;inset:0;z-index:0;pointer-events:none;
  background-image:linear-gradient(rgba(31,78,121,.035) 1px,transparent 1px),
  linear-gradient(90deg,rgba(31,78,121,.035) 1px,transparent 1px);background-size:32px 32px}
#progress{position:fixed;top:0;left:0;height:3px;width:0;z-index:60;background:var(--rust);transition:width .1s linear}
.shell{position:relative;z-index:1;display:flex;max-width:1240px;margin:0 auto}
nav.toc{width:288px;flex:0 0 288px;align-self:flex-start;position:sticky;top:0;height:100vh;
  padding:40px 26px 40px 34px;overflow-y:auto;border-right:1px solid var(--line)}
main{flex:1 1 auto;min-width:0;padding:64px 56px 140px;max-width:calc(var(--maxw) + 112px)}
.brandmark{font-family:"JetBrains Mono",monospace;font-size:11px;letter-spacing:.22em;
  text-transform:uppercase;color:var(--blueprint-soft);margin-bottom:6px}
.brandtitle{font-family:"Fraunces",serif;font-weight:700;font-size:22px;line-height:1.15;margin:0 0 26px}
.toc h4{font-family:"JetBrains Mono",monospace;font-size:10px;letter-spacing:.2em;
  text-transform:uppercase;color:var(--ink-soft);margin:0 0 12px;font-weight:600}
.toc ol{list-style:none;margin:0;padding:0} .toc li{margin:0}
.toc a{display:flex;gap:11px;align-items:baseline;padding:7px 10px;margin:1px 0;border-radius:7px;
  text-decoration:none;color:var(--ink-soft);font-family:"JetBrains Mono",monospace;font-size:12.5px;
  line-height:1.35;transition:background .15s,color .15s}
.toc a .n{color:var(--blueprint-soft);font-weight:600;flex:0 0 22px}
.toc a:hover{background:var(--blueprint-wash);color:var(--ink)}
.toc a.active{background:var(--blueprint);color:#fff} .toc a.active .n{color:#bcd3e8}
.lessonmeta{display:flex;align-items:center;gap:14px;margin-bottom:18px;font-family:"JetBrains Mono",monospace;
  font-size:12px;letter-spacing:.15em;text-transform:uppercase;color:var(--rust)}
.lessonmeta .num{display:inline-grid;place-items:center;width:54px;height:54px;border:2px solid var(--rust);
  border-radius:50%;font-family:"Fraunces",serif;font-weight:700;font-size:24px;letter-spacing:0;color:var(--rust)}
h1{font-family:"Fraunces",serif;font-weight:900;font-size:clamp(38px,5.5vw,60px);line-height:1.02;
  letter-spacing:-.015em;margin:0 0 22px}
.lede{font-size:21px;color:var(--ink-soft);max-width:62ch;margin:0 0 14px}
.disclaimer{margin-top:30px;padding:16px 20px;border-radius:10px;background:var(--paper-2);
  border:1px solid var(--line);font-size:15px;color:var(--ink-soft);line-height:1.55}
.disclaimer strong{color:var(--ink)}
.rule{height:1px;background:var(--line-strong);border:none;margin:54px 0}
section{scroll-margin-top:28px;margin-top:64px}
.steptag{display:inline-flex;align-items:center;gap:9px;margin-bottom:14px;font-family:"JetBrains Mono",monospace;
  font-size:11px;letter-spacing:.18em;text-transform:uppercase;color:var(--blueprint-soft)}
.steptag b{display:inline-grid;place-items:center;min-width:30px;height:30px;padding:0 7px;
  background:var(--blueprint);color:#fff;border-radius:6px;font-weight:600;letter-spacing:.05em}
h2{font-family:"Fraunces",serif;font-weight:700;font-size:clamp(27px,3.6vw,36px);line-height:1.1;
  letter-spacing:-.01em;margin:0 0 18px}
h3{font-family:"Fraunces",serif;font-weight:600;font-size:21px;margin:34px 0 10px}
p{margin:0 0 18px} main a{color:var(--blueprint);text-underline-offset:2px}
strong{font-weight:600;color:var(--ink)}
code{font-family:"JetBrains Mono",monospace;font-size:.82em;background:var(--blueprint-wash);
  color:var(--blueprint);padding:1px 6px;border-radius:5px}
ul{margin:0 0 18px;padding-left:0;list-style:none} ul li{position:relative;padding-left:24px;margin-bottom:9px}
ul li::before{content:"";position:absolute;left:4px;top:.66em;width:7px;height:7px;background:var(--rust);
  border-radius:1.5px;transform:rotate(45deg)}
figure{margin:30px 0}
.blueprint{background:linear-gradient(rgba(31,78,121,.06) 1px,transparent 1px),
  linear-gradient(90deg,rgba(31,78,121,.06) 1px,transparent 1px),var(--paper-2);
  background-size:18px 18px,18px 18px,auto;border:1px solid var(--line-strong);border-radius:12px;padding:26px 22px 18px}
.blueprint svg{display:block;width:100%;height:auto}
figcaption{margin-top:12px;font-family:"JetBrains Mono",monospace;font-size:11.5px;color:var(--ink-soft);text-align:center}
.lbl{font-family:"JetBrains Mono",monospace;font-size:13px;fill:var(--ink);font-weight:500}
.lbl-sm{font-family:"JetBrains Mono",monospace;font-size:11px;fill:var(--ink-soft)}
.flow{stroke:var(--blueprint);stroke-width:2;fill:none}
.flow-r{stroke:var(--rust);stroke-width:2;fill:none;stroke-dasharray:5 4}
.flow-d{stroke:var(--blueprint-soft);stroke-width:1.5;fill:none;stroke-dasharray:3 4}
.callout{margin:26px 0;padding:18px 22px;border-radius:10px;border-left:4px solid var(--blueprint);
  background:var(--blueprint-wash);font-size:17px}
.callout .k{display:block;font-family:"JetBrains Mono",monospace;font-size:11px;letter-spacing:.16em;
  text-transform:uppercase;color:var(--blueprint);margin-bottom:7px;font-weight:600}
.callout.tip{border-left-color:var(--rust);background:var(--rust-wash)} .callout.tip .k{color:var(--rust)}
.callout p:last-child{margin-bottom:0}
.vs{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin:26px 0}
.vs .col{background:var(--paper-2);border:1px solid var(--line);border-radius:10px;padding:18px 20px}
.vs h4{font-family:"Fraunces",serif;font-size:18px;font-weight:600;margin:0 0 12px}
.vs ul{margin:0} .vs li{font-size:15.5px;line-height:1.5}
.takeaways{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:14px;margin-top:24px}
.tk{background:var(--paper-2);border:1px solid var(--line);border-radius:10px;padding:16px 18px}
.tk .num{font-family:"JetBrains Mono",monospace;font-size:11px;color:var(--rust);letter-spacing:.1em}
.tk b{display:block;font-family:"Fraunces",serif;font-size:17px;margin:4px 0 5px}
.tk span{font-size:14.5px;color:var(--ink-soft);line-height:1.45}
footer{margin-top:70px;padding-top:26px;border-top:1px solid var(--line-strong);
  font-family:"JetBrains Mono",monospace;font-size:12px;color:var(--ink-soft);line-height:1.7}
/* interactive stepper */
.stepper .stepcap{display:flex;gap:10px;align-items:baseline;margin-top:16px;flex-wrap:wrap}
.stepper .stepnum{font-family:"JetBrains Mono",monospace;font-size:11px;letter-spacing:.08em;color:var(--rust);
  white-space:nowrap;border:1px solid var(--rust);border-radius:20px;padding:3px 11px}
.stepper .steptext{font-family:"Newsreader",serif;font-size:16px;color:var(--ink);line-height:1.4;flex:1;min-width:220px}
.stepper .controls{display:flex;gap:8px;flex-wrap:wrap;align-items:center;margin-top:14px}
.stepper .controls button{font-family:"JetBrains Mono",monospace;font-size:12px;cursor:pointer;
  border:1px solid var(--line-strong);background:var(--paper-2);color:var(--ink);padding:7px 13px;border-radius:8px;
  transition:background .15s,border-color .15s,transform .05s}
.stepper .controls button:hover{background:var(--blueprint-wash);border-color:var(--blueprint-soft)}
.stepper .controls button:active{transform:translateY(1px)}
.stepper .controls [data-act="play"]{background:var(--blueprint);color:#fff;border-color:var(--blueprint);min-width:96px}
.st{transition:opacity .3s ease} .st.dim{opacity:.16}
.packet{filter:drop-shadow(0 1px 2px rgba(0,0,0,.3))}
/* DSA array + pointer primitives */
.cell{fill:var(--paper-2);stroke:var(--line-strong);stroke-width:1.6;transition:fill .25s ease,stroke .25s ease,opacity .25s ease}
.cell.lo{fill:var(--blueprint-wash);stroke:var(--blueprint);stroke-width:2.6}
.cell.hi{fill:#FBEEDB;stroke:var(--amber);stroke-width:2.6}
.cell.ok{fill:#E6F1DF;stroke:var(--green);stroke-width:2.6}
.cell.faint{opacity:.34}
.cellv{font-family:"JetBrains Mono",monospace;font-size:18px;font-weight:600;fill:var(--ink);transition:opacity .2s}
.celli{font-family:"JetBrains Mono",monospace;font-size:10.5px;fill:var(--ink-soft)}
.ptrmark{transition:transform .35s cubic-bezier(.4,0,.2,1)}
.ptrmark text{font-family:"JetBrains Mono",monospace;font-size:12px;font-weight:600}
.ptrmark.lo path{fill:var(--blueprint)} .ptrmark.lo text{fill:var(--blueprint)}
.ptrmark.hi path{fill:var(--amber)} .ptrmark.hi text{fill:#9a6515}
.llnode{fill:var(--paper-2);stroke:var(--blueprint-soft);stroke-width:2;transition:fill .25s,stroke .25s}
.llnode.meet{fill:#E6F1DF;stroke:var(--green);stroke-width:2.8}
.readout{font-family:"JetBrains Mono",monospace;font-size:14.5px;fill:var(--ink)}
/* practice ladder */
.ladder{margin:24px 0;display:flex;flex-direction:column;gap:11px}
.drill{border:1px solid var(--line);border-radius:11px;background:var(--paper-2);padding:14px 18px}
.drill .top{display:flex;align-items:center;gap:11px;flex-wrap:wrap;margin-bottom:3px}
.pill{font-family:"JetBrains Mono",monospace;font-size:10px;letter-spacing:.07em;text-transform:uppercase;
  padding:3px 9px;border-radius:20px;font-weight:600;white-space:nowrap}
.pill.e{background:#E6F1DF;color:#3f7a2e} .pill.m{background:#FBEEDB;color:#9a6515} .pill.h{background:var(--rust-wash);color:var(--rust)}
.drill .nm{font-family:"Fraunces",serif;font-weight:600;font-size:18px;color:var(--ink)}
.drill .tag{font-family:"JetBrains Mono",monospace;font-size:10.5px;color:var(--blueprint-soft);margin-left:auto;letter-spacing:.04em}
.drill p{margin:4px 0 0;font-size:16px}
.drill .idea{font-size:14.5px;color:var(--ink-soft);margin-top:7px;line-height:1.5}
.drill .idea b{color:var(--blueprint);font-family:"JetBrains Mono",monospace;font-size:10.5px;letter-spacing:.08em;text-transform:uppercase;margin-right:6px}
/* worked problem (LeetCode walkthrough) */
.worked{margin:30px 0;border:1px solid var(--line-strong);border-radius:14px;background:var(--paper-2);overflow:hidden;box-shadow:0 1px 0 rgba(31,78,121,.04)}
.worked .whead{display:flex;align-items:center;gap:11px;flex-wrap:wrap;padding:14px 22px;background:var(--blueprint-wash);border-bottom:1px solid var(--line)}
.worked .wk{font-family:"JetBrains Mono",monospace;font-size:10.5px;letter-spacing:.18em;text-transform:uppercase;color:var(--blueprint);font-weight:600}
.worked .lc{font-family:"JetBrains Mono",monospace;font-size:11px;color:var(--ink-soft);border:1px solid var(--line-strong);border-radius:20px;padding:3px 10px;margin-left:auto;white-space:nowrap}
.worked .wbody{padding:4px 22px 20px}
.worked .wname{font-family:"Fraunces",serif;font-weight:600;font-size:22px;color:var(--ink);margin:18px 0 7px}
.worked .wprompt{font-size:16.5px;color:var(--ink);margin:0}
.worked .wh{font-family:"JetBrains Mono",monospace;font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:var(--rust);font-weight:600;margin:22px 0 6px}
.wsteps{margin:6px 0 4px;border-left:2px solid var(--line-strong)}
.ws{padding:0 0 0 16px;margin:0 0 13px} .ws:last-child{margin-bottom:0}
.wsk{display:block;font-family:"JetBrains Mono",monospace;font-size:10px;letter-spacing:.13em;text-transform:uppercase;color:var(--blueprint);font-weight:600;margin-bottom:3px}
.ws p{margin:0;font-size:16.5px;line-height:1.55} .ws p b{color:var(--ink)}
.codetag{font-family:"JetBrains Mono",monospace;font-size:9.5px;letter-spacing:.16em;text-transform:uppercase;color:var(--ink-soft);margin:0 0 6px}
pre.code{margin:0 0 4px;background:#FBF7EE;border:1px solid var(--line-strong);border-left:3px solid var(--blueprint-soft);border-radius:10px;padding:15px 18px;overflow-x:auto;line-height:1.6}
pre.code code{font-family:"JetBrains Mono",monospace;font-size:13px;background:none;color:#2c2a25;padding:0;border-radius:0;display:block;white-space:pre}
pre.code .cm{color:#9a8e76;font-style:italic} pre.code .kw{color:var(--rust);font-weight:600}
pre.code .fn{color:var(--blueprint);font-weight:600} pre.code .lit{color:var(--violet)}
.say{margin:18px 0 0;padding:16px 20px;border-radius:10px;background:var(--rust-wash);border-left:4px solid var(--rust)}
.say .k{display:block;font-family:"JetBrains Mono",monospace;font-size:11px;letter-spacing:.16em;text-transform:uppercase;color:var(--rust);margin-bottom:8px;font-weight:600}
.say p{margin:0 0 10px;font-size:16px;font-style:italic;color:var(--ink);line-height:1.55} .say p:last-child{margin-bottom:0}
.say .plain{font-style:normal;color:var(--ink-soft);font-size:14.5px}
.menubtn{display:none}
@media(max-width:980px){
  nav.toc{position:fixed;z-index:50;top:0;left:0;height:100vh;width:280px;background:var(--paper);
    transform:translateX(-105%);transition:transform .28s ease;box-shadow:0 0 40px rgba(0,0,0,.12)}
  nav.toc.open{transform:translateX(0)}
  main{padding:78px 22px 100px}
  .menubtn{display:flex;align-items:center;gap:8px;position:fixed;z-index:55;top:14px;left:14px;
    background:var(--blueprint);color:#fff;border:none;border-radius:9px;padding:9px 14px;
    font-family:"JetBrains Mono",monospace;font-size:12px;cursor:pointer}
  body{font-size:18px} .vs{grid-template-columns:1fr} .drill .tag{margin-left:0}
  .worked .lc{margin-left:0} .worked .wbody{padding:4px 16px 18px} pre.code code{font-size:12.5px}
}
@media(max-width:520px){main{padding:74px 16px 90px} h1{font-size:33px}}
```

### Arrow markers (place once near the top of `<body>`)

```html
<svg width="0" height="0" style="position:absolute" aria-hidden="true"><defs>
  <marker id="arrow" markerWidth="9" markerHeight="9" refX="7.5" refY="4.5" orient="auto"><path d="M0,0 L9,4.5 L0,9 z" fill="#1F4E79"/></marker>
  <marker id="arrow-r" markerWidth="9" markerHeight="9" refX="7.5" refY="4.5" orient="auto"><path d="M0,0 L9,4.5 L0,9 z" fill="#B0532F"/></marker>
  <marker id="arrow-s" markerWidth="8" markerHeight="8" refX="6.5" refY="4" orient="auto"><path d="M0,0 L8,4 L0,8 z" fill="#4A7BA6"/></marker>
  <marker id="arrow-a" markerWidth="9" markerHeight="9" refX="7.5" refY="4.5" orient="auto"><path d="M0,0 L9,4.5 L0,9 z" fill="#C98A2B"/></marker>
</defs></svg>
```

### Minimal JS (progress bar, scroll-spy nav, mobile drawer)

```js
var bar=document.getElementById('progress');
function onScroll(){var h=document.documentElement,m=h.scrollHeight-h.clientHeight;
  bar.style.width=(m>0?h.scrollTop/m*100:0)+'%';}
addEventListener('scroll',onScroll,{passive:true});onScroll();
var links=[].slice.call(document.querySelectorAll('.toc a')),map={};
links.forEach(function(a){map[a.getAttribute('href').slice(1)]=a;});
var obs=new IntersectionObserver(function(es){es.forEach(function(e){if(e.isIntersecting){
  links.forEach(function(l){l.classList.remove('active')});
  if(map[e.target.id])map[e.target.id].classList.add('active');}})},{rootMargin:'-20% 0px -70% 0px'});
document.querySelectorAll('section').forEach(function(s){obs.observe(s);});
var toc=document.getElementById('toc'),btn=document.getElementById('menubtn');
if(btn){btn.onclick=function(){toc.classList.toggle('open')};
  toc.onclick=function(e){if(e.target.closest('a'))toc.classList.remove('open')};}
```

---

## Interview-optimization rules

- **State the brute force and its big-O first.** Open each section with the
  naive solution and why it is too slow or too memory-heavy. Never feature-dump.
- **Name the pattern.** The candidate should be able to say "this is a two
  pointers / sliding window / monotonic-stack problem" on sight — train that.
- **State and maintain the invariant.** The one sentence that is always true
  (e.g. *the answer lies between `L` and `R`*, *everything in `a[0…slow]` is
  finalized*) is both the correctness proof and the debugging tool. Make it
  explicit.
- **Always give time AND space complexity**, and surface the trade-off with a
  `.vs` table where there is a real decision (two pointers vs hash map; sort
  first vs hash; recursion vs iteration; heap vs full sort).
- **Call the edge cases by name.** Empty input, single element, all-equal
  values, duplicates, negative numbers, integer overflow, an empty/one-node
  list, a self-loop, an already-sorted or reverse-sorted array. Interviewers
  probe these constantly.
- **End with the interviewer's next question.** Use a `.callout.tip` to flag the
  natural follow-up (the harder variant, the unsorted case, "find the index not
  just the value") so the reader rehearses it.
- **Work one real problem per technique, end to end.** Each technique section
  carries a `.worked` block: a named LeetCode problem reasoned out linearly
  (restate → brute force + big-O → the waste → the move → invariant + cost),
  followed by the actual code and a first-person script for narrating it to the
  interviewer (closing with the edge cases to dry-run). Seeing the pattern
  become real, defendable code is what converts recognition into a passable
  live-coding answer. Write the prompt, reasoning, code, and narration yourself;
  verify the code runs.
- **Force active recall.** Every lesson ends with the practice ladder *and* a
  5-6 question self-test targeting the *why* and *when* of each variant.
- **Encourage timed, on-paper, no-autocomplete practice** — that mirrors a real
  live-coding round; tell the reader to dry-run each algorithm by hand and
  redraw each figure from memory.
- If the user names a target company or region, lean the framing toward what
  that employer is known for (in **Singapore**: Grab, Sea/Shopee, GovTech,
  ByteDance/TikTok, the big-tech offices, and the banks all run standard
  LeetCode-style live-coding rounds), but keep the technique itself general.

---

## Course map (canonical — matches `dsa-roadmap.html`)

A pattern-first path of original lessons, numbered **L00–L41** across nine
phases. **This numbering is the single source of truth and matches the roadmap
index `dsa-roadmap.html`.** Generate a lesson by its number *and* title
(e.g. "generate L19 — Backtracking"); always key off the title, since the
number is just a label. Markers: **★** = the **Core 15** (highest-yield, do
first); **▹** = **Stretch** (advanced long tail — skip unless targeting the
hardest Google/TikTok loops); **◇** = **concept lesson** (lighter variant — see
*Concept lessons* under Lesson structure).

- **P0 · Interview OS** — ◇★ L00 Problem-Solving Framework (UMPIRE) · ◇★ L01 Complexity Analysis (Big-O)
- **P1 · Core Data Structures** — ◇ L02 Arrays & Strings · ◇★ L03 Hash Maps & Sets · ◇ L04 Linked Lists · ◇ L05 Stacks & Queues · ◇ L06 Trees & BSTs · ◇ L07 Heaps / Priority Queues · ◇ L08 Graph Representations · ▹ L09 Tries
- **P2 · Two-Pointer & Window** — ★ L10 Two Pointers · L11 Fast & Slow Pointers · ★ L12 Sliding Window · L13 Prefix Sum & Difference Array
- **P3 · Searching & Sorting** — ★ L14 Binary Search · L15 Binary Search on the Answer · L16 Sorting & Custom Comparators · ▹ L17 Cyclic Sort / Index as Hash
- **P4 · Recursion, Backtracking, Trees** — L18 Recursion & Divide-and-Conquer · ★ L19 Backtracking · ★ L20 Tree DFS & BFS Patterns · L21 BST Patterns · ▹ L22 Tree Construction & Serialization
- **P5 · Graph Patterns** — ★ L23 Graph Traversal (BFS & DFS) · ★ L24 Topological Sort · ★ L25 Union-Find (DSU) · L26 Shortest Path (Dijkstra & 0-1 BFS) · ▹ L27 Advanced Graphs (MST & more)
- **P6 · Heap, Intervals & Greedy** — ★ L28 Top-K & Two Heaps · ★ L29 Intervals · L30 Greedy
- **P7 · Dynamic Programming** — ★ L31 DP Foundations (1D) · L32 Grid & 2D DP · L33 Knapsack DP · L34 Subsequence DP · ▹ L35 State-Machine & Interval DP · ▹ L36 Bitmask DP
- **P8 · Specialized & Advanced** — ★ L37 Monotonic Stack & Queue · L38 Bit Manipulation · ▹ L39 Math & Number Theory · ▹ L40 Segment Tree & Fenwick (BIT) · ▹ L41 String Algorithms (KMP & Rabin-Karp)

Keep the design system identical across all lessons so the set feels like one
course. Natural follow-ons: Sliding Window (L12) after Two Pointers (L10) — they
are siblings; the DP family (L31 → L34) in order. When several lessons are
requested, also offer the roadmap `index.html` that links them together.

---

## Workflow when this skill triggers

1. Identify the single pattern — or concept (see *Concept lessons*) — for this
   lesson (ask only if genuinely ambiguous).
2. Read the relevant frontend-design guidance, and — if the system-design or a
   prior DSA lesson is available — open it to match the exact look, the diagram
   patterns, and the shared engine. Then outline the lesson as a
   bottleneck-driven sequence (brute force → insight → invariant) of 5-7
   sections, deciding which ~3 figures are genuinely sequential (interactive)
   and which are static comparisons.
3. Write original prose for each section; add an SVG per major concept using the
   building blocks above (`buildRow`/`setCells`/`_mv` for arrays & pointers,
   `llnode`/`flow`/`flow-r` for lists); add trade-off tables and callouts. Then,
   for **each technique section, add one `.worked` block** — pick a named
   LeetCode problem that the section's figure illustrates (or a sibling of it),
   and write the original prompt, the "think it through" reasoning chain, the
   code, and the interviewer narration script. Confirm the code is correct.
4. Build the **practice ladder** (real problems, original one-line prompts,
   graded Easy→Medium→Hard, each tagged with its variant and target complexity)
   and the **self-test**.
5. Assemble into one self-contained HTML file with the design system + arrow
   markers + the minimal JS + the `makeStepper` engine + the DSA helpers.
6. Save to the outputs directory and present it. Offer to generate the next
   pattern lesson (Sliding Window is the obvious follow-on) or an `index.html`
   that links the course together.

**Shared assets note:** the design-system CSS, the arrow-marker defs, and the
`makeStepper` engine are intentionally identical to the `system-design-study-guide`
skill. Reuse them verbatim so a learner moving between the System Design course
and the DSA course feels they are in one product; only the SVG *content* (data
structures and pointers instead of servers and databases) and the added
DSA/ladder CSS classes differ.
