---
layout: 'layouts/doc-post.njk'
title: Total Blocking Time
description: |
  Learn about Lighthouse's Total Blocking Time metric and
  how to measure and optimize it.
date: 2019-10-09
updated: 2021-06-04
---

Total Blocking Time (TBT) is one of the metrics tracked in the **Performance** section
of the Lighthouse report. Each metric captures some aspect of page load speed.

The Lighthouse report displays TBT in milliseconds:

<figure>
  {% Img src="image/MtjnObpuceYe3ijODN3a79WrxLU2/wk3OTIdxFPoUImDCnjic.png", alt="A screenshot of the Lighthouse Total Blocking Time audit", width="800", height="592" %}
</figure>

## What TBT measures

TBT measures the total amount of time that a page is blocked from responding to user input,
such as mouse clicks, screen taps, or keyboard presses. The sum is calculated by adding
the _blocking portion_ of all [long tasks] between [First Contentful Paint][fcp] and [Time to Interactive][tti].
Any task that executes for more than 50&nbsp;ms is a long task. The amount of time after
50&nbsp;ms is the blocking portion. For example, if Lighthouse detects a 70&nbsp;ms long task,
the blocking portion would be 20&nbsp;ms.

## How Lighthouse determines your TBT score

Your TBT score is a comparison of your page's TBT time and TBT times millions of real sites
when loaded on mobile devices. See [How metric scores are determined](/docs/lighthouse/performance/performance-scoring/#metric-scores)
to learn how Lighthouse score thresholds are set.

This table shows how to interpret your TBT score:

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>TBT time<br>(in milliseconds)</th>
        <th>Color-coding</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>0–200</td>
        <td>Green (fast)</td>
      </tr>
      <tr>
        <td>200-600</td>
        <td>Orange (moderate)</td>
      </tr>
      <tr>
        <td>Over 600</td>
        <td>Red (slow)</td>
      </tr>
    </tbody>
  </table>
</div>

{% Partial 'lighthouse-performance/scoring.njk' %}

## How to improve your TBT score

See [What is causing my long tasks?](https://web.dev/long-tasks-devtools/#what-is-causing-my-long-tasks) to learn
how to diagnose the root cause of long tasks with the Performance panel of Chrome DevTools.

In general, the most common causes of long tasks are:

- Unnecessary JavaScript loading, parsing, or execution. While analyzing your code in the Performance panel
  you might discover that the main thread is doing work that isn't really necessary to load the page.
  [Reducing JavaScript payloads with code splitting][split], [removing unused code][unused], or
  [efficiently loading third-party JavaScript][3p] should improve your TBT score.
- Inefficient JavaScript statements. For example, after analyzing your code in the Performance panel, suppose
  you see a call to `document.querySelectorAll('a')` that returns 2000 nodes. Refactoring your code to
  use a more specific selector that only returns 10 nodes should improve your TBT score.

{% Aside %}
Unnecessary JavaScript loading, parsing, or execution is usually a much bigger opportunity for improvement
on most sites.
{% endAside %}

{% Partial 'lighthouse-performance/improve.njk' %}

## Resources

- [Source code for **Total Blocking Time** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/metrics/total-blocking-time.js)
- [Are long JavaScript tasks delaying your Time to Interactive?][long tasks]
- [Optimize First Input Delay][optimize fid]
- [First Contentful Paint][fcp]
- [Time to Interactive][tti]
- [Reduce JavaScript payloads with code splitting][split]
- [Remove unused code][unused]
- [Efficiently load third-party resources][3p]

[long tasks]: https://web.dev/long-tasks-devtools/
[optimize fid]: https://web.dev/optimize-fid/
[fcp]: https://web.dev/fcp/
[tti]: https://web.dev/interactive/
[split]: https://web.dev/reduce-javascript-payloads-with-code-splitting/
[unused]: https://web.dev/remove-unused-code/
[3p]: https://web.dev/efficiently-load-third-party-javascript/
