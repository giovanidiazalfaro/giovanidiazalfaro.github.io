---
layout: page
title: Turning a cognitive task analysis into design questions engineers could test
description: "Three design recommendations for managing pilot workload, adopted into Lockheed's engineering design process."
kicker: "Case study 1 of 3"
permalink: /case-studies/lockheed/
image:
page_nav: true
---

<div class="cs-header">
  <p class="cs-header__project">Externalized and Extended Cognition: Cognitive Offloading for Manned-Unmanned Teaming</p>
  <p class="cs-header__meta">Lockheed Martin, Future Vertical Lift, 2023 – 2026. Role: Research Lead</p>
</div>

<div class="cs-stats">
  <div class="cs-stat"><span class="cs-stat__value">3 of 3</span><span class="cs-stat__label">design recommendations adopted into Lockheed's engineering design process</span></div>
  <div class="cs-stat"><span class="cs-stat__value">UI overhaul</span><span class="cs-stat__label">of an active operations system, informed by the findings</span></div>
  <div class="cs-stat"><span class="cs-stat__value">HFES 2024</span><span class="cs-stat__label">first-author paper and presentation, <a href="https://doi.org/10.1177/10711813241275506">doi.org/10.1177/10711813241275506</a></span></div>
</div>

## The problem as it was handed to me

Lockheed Martin needed to understand how to reduce pilot cognitive workload in next-generation manned-unmanned aviation, the Future Vertical Lift program. A detailed cognitive task analysis of the operational environment already existed. What was missing was a bridge from what pilots need cognitively to concrete, testable design questions that engineers could act on.

<figure class="cs-figure">
  <img src="/images/case-studies/lockheed-problem-triad.png" alt="Slide titled Cognition is no longer held within the pilot, nor the cockpit. The broad goal, reduce pilot cognitive workload, is restated as a goal engineers can design against. A triangle links pilot, aircraft systems, and unmanned teammates, which are traditionally treated as three separate design problems." loading="lazy" width="2502" height="1197">
  <figcaption>The starting point. Pilot, aircraft systems, and unmanned teammates, traditionally treated as three separate design problems. <a class="cs-fullsize" href="/images/case-studies/lockheed-problem-triad.png" target="_blank" rel="noopener">Open full size<span class="sr-only"> image (opens in new tab)</span></a></figcaption>
</figure>

## The choice I made, and why

I could have treated workload as one thing to measure and minimize. Instead I applied a cognitive science framework, 4E cognition, which treats cognition as extended, embedded, enactive, and embodied. It let me ask a more useful question. Not only how much workload there is, but where the cognitive processing lives: in the pilot, in the system, or in the interaction between them. That pointed to two separable mechanisms that engineers could design around independently.

<figure class="cs-figure cs-anim" id="cognitive-unit-anim">
  <div class="cs-anim__frame">
    <img class="cs-anim__img no-lightense" src="/images/case-studies/lockheed-cognitive-units-separate.png" data-gif="/images/case-studies/lockheed-cognitive-unit-merge.gif" data-end="/images/experience/lockheed-cognitive-unit-merged.png" alt="Environment, system, and pilot shown as three separate cognitive units, which then merge into one cognitive unit." width="1100" height="568">
    <button type="button" class="cs-anim__btn" hidden><i class="fa-solid fa-rotate-right" aria-hidden="true"></i> <span>Replay</span></button>
  </div>
  <figcaption>The reframe. Environment, system, and pilot treated as one cognitive unit.</figcaption>
</figure>

<script>
(function () {
  var fig = document.getElementById('cognitive-unit-anim');
  if (!fig) return;
  var img = fig.querySelector('.cs-anim__img');
  var btn = fig.querySelector('.cs-anim__btn');
  var label = btn.querySelector('span');
  var gif = img.getAttribute('data-gif');
  var end = img.getAttribute('data-end');
  var LENGTH = 6200; /* the GIF is 120 frames at 50 ms and plays once */
  var timer;
  var playing = false;
  var icon = btn.querySelector('i');

  function setButton(text, iconClass) {
    label.textContent = text;
    icon.className = 'fa-solid ' + iconClass;
    btn.hidden = false;
  }

  function finish() {
    clearTimeout(timer);
    playing = false;
    img.src = end;
    setButton('Replay', 'fa-rotate-right');
  }

  function play() {
    clearTimeout(timer);
    playing = true;
    img.src = gif + '?play=' + Date.now(); /* new URL restarts the GIF */
    /* A Skip control while it plays, so the motion can always be stopped */
    setButton('Skip', 'fa-forward');
    timer = setTimeout(finish, LENGTH);
  }

  btn.addEventListener('click', function () { playing ? finish() : play(); });

  var reduce = window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  if (reduce || !('IntersectionObserver' in window)) {
    /* No autoplay. Show the end state and let the reader start it. */
    img.src = end;
    setButton('Play animation', 'fa-play');
    return;
  }

  var io = new IntersectionObserver(function (entries) {
    entries.forEach(function (e) {
      if (e.isIntersecting) { play(); io.disconnect(); }
    });
  }, { threshold: 0.6 });
  io.observe(img);
})();
</script>

<figure class="cs-figure">
  <img src="/images/case-studies/lockheed-offloading-scaffolding.png" alt="Slide titled Two separable design levers. Offloading moves internal processing out, onto the system or the environment. Scaffolding is external support that mediates processes without removing the task from the human." loading="lazy" width="2547" height="1240">
  <figcaption>The two design levers. Offloading moves processing out of the pilot's head. Scaffolding supports the decision without taking it away. <a class="cs-fullsize" href="/images/case-studies/lockheed-offloading-scaffolding.png" target="_blank" rel="noopener">Open full size<span class="sr-only"> image (opens in new tab)</span></a></figcaption>
</figure>

## How I worked with the engineers

I facilitated working sessions with Lockheed and partner engineering teams to align on objectives and turn their goals into research questions. I also ran usability testing on an operations monitoring and information management system.

## What I produced

Three recommendations that turn the framework into testable design questions, and the experiments to test them.

1. **Look at the whole timeline.** Analyze workload across planning, the mission, and the debrief, since each one shapes the next.
2. **Vary how available offloading is.** Test it as required, optional, and unavailable, to see how that choice affects cognitive efficiency when tasks are disrupted.
3. **Study the interactions.** Examine how types of workload and offloading techniques combine, and what that does to mission performance.

<figure class="cs-figure">
  <img src="/images/case-studies/lockheed-three-recommendations.png" alt="Slide titled From question to recommendation. Three questions the reframe made askable lead to three recommendations. Analyze the full mission timeline. Test offloading at varied accessibility. Study workload type by offloading technique." loading="lazy" width="2504" height="1212">
  <figcaption>From question to recommendation. <a class="cs-fullsize" href="/images/case-studies/lockheed-three-recommendations.png" target="_blank" rel="noopener">Open full size<span class="sr-only"> image (opens in new tab)</span></a></figcaption>
</figure>

<figure class="cs-figure">
  <img src="/images/case-studies/lockheed-study-designs.png" alt="Slide titled From recommendation to study design. Each of the three recommendations is paired with a study, what it measures, the instruments that measure it, and the decision it resolves." loading="lazy" width="2540" height="1167">
  <figcaption>From recommendation to study design. Each study names what to vary, what to measure, and the instrument that measures it. <a class="cs-fullsize" href="/images/case-studies/lockheed-study-designs.png" target="_blank" rel="noopener">Open full size<span class="sr-only"> image (opens in new tab)</span></a></figcaption>
</figure>

<figure class="cs-figure">
  <img src="/images/case-studies/lockheed-testbed-panels.png" alt="Slide titled Empirical examination of offloading and workload characteristics. Four panels from the UCF Cognitive Sciences Laboratory. Understanding the nature of cognitive workload. Offloading and replanning. Workload, offloading and replanning, integrated. 4E cognitive work analysis for cockpit design." loading="lazy" width="2546" height="1193">
  <figcaption>From recommendations to examinations, at the UCF Cognitive Sciences Laboratory. <a class="cs-fullsize" href="/images/case-studies/lockheed-testbed-panels.png" target="_blank" rel="noopener">Open full size<span class="sr-only"> image (opens in new tab)</span></a></figcaption>
</figure>

## What's still open

The hardest part was not the theory. It was translating it into something an engineer outside cognitive science could act on without oversimplifying it. Next time I would ask engineers for feedback on the recommendations earlier, before finalizing the experimental designs, to catch translation gaps sooner.

<p class="cs-footnote">Implementation details are confidential and omitted.</p>

<div class="cs-footer">
  <a href="/Experience/">← Back to Experience</a>
  <a href="/case-studies/orlando-health/">Next case study: Orlando Health →</a>
  <a class="cs-pdf-link" href="/files/GDA_2026_Case_Studies.pdf" target="_blank" rel="noopener"><i class="fa-solid fa-file-pdf" aria-hidden="true"></i> Download all three as a PDF<span class="sr-only"> (opens in new tab)</span></a>
</div>
