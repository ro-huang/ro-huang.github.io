---
layout: page
title: "/research"
permalink: /research
---

<style>
.theme-box {
  border: 2px solid #3e2723;
  padding: 1.5em;
  margin-bottom: 2em;
  background-color: #f5e6d3;
}

.theme-box h3 {
  margin-top: 0;
  margin-bottom: 0.5em;
}

.section-narrative {
  margin-bottom: 1.5em;
  line-height: 1.6;
}

.section-narrative p {
  margin: 0.5em 0;
}

.project-card {
  border: 1px solid #3e2723;
  padding: 1em;
  margin-bottom: 1em;
}

.project-card:last-child {
  margin-bottom: 0;
}

.project-header {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  gap: 0.5em;
  margin-bottom: 0.5em;
}

.project-title {
  font-weight: bold;
  margin: 0;
}

.project-badge {
  font-size: 0.75em;
  padding: 0.15em 0.5em;
  border: 1px solid #3e2723;
  background-color: #f5e6d3;
}

.project-badge.in-progress {
  border-style: dashed;
}

.project-tags {
  font-size: 0.8em;
  color: #6d5147;
}

.project-description {
  margin: 0.5em 0;
  font-size: 0.95em;
}

.project-description p {
  margin: 0.5em 0;
}

.publications-list {
  font-size: 0.85em;
  margin-top: 0.75em;
  padding-top: 0.5em;
  border-top: 1px dashed #ccc;
}

.publications-list ul {
  margin: 0.25em 0;
  padding-left: 1.5em;
}

.publications-list li {
  margin-bottom: 0.25em;
}
</style>

My research interests are in AI behavioral eval tooling, measurement epistemology, and the economics of innovation. Below, I outline some ongoing projects as well as some of the work I've done in the past.

<!--
<div class="theme-box">

<h3>Evaluation Tooling</h3>

<div class="section-narrative">
Even when AI models perform well on safety evaluations, I'm concerned that this behavior may not hold up when models are given access to new tools or deployed in settings different from what they were tested in. This work examines whether current evaluation tools can reliably detect if models are aligned or are just performing alignment.
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Uncertainty Scores for AI Coding Agents</span>
    <span class="project-badge in-progress">In Progress</span>
    <span class="project-tags">[AI Safety]</span>
  </div>
  <div class="project-description">
    One way to think about behavior in AI agents is through how internally consistent they are. Pres et al. (2026) has a great paper on this, but we also see it empirically in e.g., Irpan et al. (2025). In this project, I examine this phenomenon in the coding agent setting and see how well agents are able to predict the pass@k rate at various benchmark problems.
  </div>
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Agent Detection for Eval Awareness</span>
    <span class="project-badge in-progress">In Progress</span>
    <span class="project-tags">[AI Safety]</span>
  </div>
  <div class="project-description">
    Current models often appear aware of the fact that they're being evaluated (Needham et al. (2025)). One dimension of this that hasn't been frequently tested is whether models are aware they are talking to other models in evals. This is especially important for multi-turn, agentic settings. In this project, I explore whether eval awareness varies depending on who the model is interacting with, and what kinds of interventions might reduce eval awareness in settings where models are interacting with other models.
  </div>
</div>

</div>
-->

<div class="theme-box">

<h3>Measurement Epistemics</h3>

<div class="section-narrative">
<p>The quality of analysis -- and by extension the findings it produces -- depends on whether the right things are being measured, and whether they're being measured well. Recently, I've been thinking about this in the context of AI agent benchmarks, in which I feel there's a need for more rigorous though about metric quality. In the past, I've thought about this in the context of health policy.</p>
<p>Though the settings are very different, my health policy work has informed how I think about AI benchmarks today, because both fields grapple with measuring inherently messy, multidimensional phenomena. In health policy, there's a strong tradition of recognizing that many metrics are just proxies for what we actually care about, and that optimizing for a proxy (like a lab value) without treating it as such can lead you away from the real goal (like patient well-being). I feel that AI benchmarks would benefit from that same discipline, since the field too often treats proxy scores as end goals without interrogating whether they truly capture the capability or behavior we're trying to measure.</p>
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Learning about progress towards automated AI R&D from CIFAR speedruns</span>
    <span class="project-badge">Blog Post</span>
    <span class="project-tags">[AI Safety]</span>
  </div>
  <div class="project-description">
    In this blog post, I give some preliminary evidence on current AI agent research capabilities by seeing whether they're able to improve a given solution to the CIFAR speedrun. I find that both Opus 4.8 and GPT 5.5 are able to make improvements, but many are marginal and they were unable to improve upon the actual SOTA solution.
  </div>
  <div class="publications-list">
    <ul>
      <li><strong>Huang, R. W.</strong> (2026). "Learning about progress towards automated AI R&D from CIFAR speedruns." <em>Blog post</em>. <a href="/technical/2026/07/05/cifar-speedrun.html">link</a></li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">MMLU-Pro Isn't Multidimensional (It Just Pretends to Be)</span>
    <span class="project-badge">Blog Post</span>
    <span class="project-tags">[AI Safety]</span>
  </div>
  <div class="project-description">
    In this blog post, I do an open-ended exporation of the dimensionality of model capabilities captured in MMLU-Pro, and consider whether asking questions across domains might improve our understanding of model abilities.
  </div>
  <div class="publications-list">
    <ul>
      <li><strong>Huang, R. W.</strong> (2025). "MMLU-Pro Isn't Multidimensional (It Just Pretends to Be)." <em>Blog post</em>. <a href="/technical/2025/11/22/mmlu.html">link</a></li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Healthcare Use and Caregiver Costs</span>
    <span class="project-badge">Published</span>
    <span class="project-tags">[Health Policy]</span>
  </div>
  <div class="project-description">
    These projects explored the effectiveness of an intervention that sought to support informal caregivers in rural communities. Informal caregiving is a particularly interesting phenomenon in health policy, since its effects are not well-captured by traditional sources of economic data. One thing that stood out to me was how to quantify the reduction in time spent in leisure. It's easier to quantify how much salary is lost by caregivers from not being able to go to work, but the loss of leisure time can also be a serious problem, and isn't easily captured in out-of-pocket costs.
  </div>
  <div class="publications-list">
    <ul>
      <li>Kaufman, B. G., <strong>Huang, R. W.</strong>, et al. (2024). <em>J Am Geriatr Soc</em> 72(8). <a href="https://doi.org/10.1111/jgs.18934">doi</a></li>
      <li>Kaufman, B. G., Zhang, W., ..., <strong>Huang, R. W.</strong>, et al. (2024). <em>J Pain Symptom Manage</em> 68(6). <a href="https://doi.org/10.1016/j.jpainsymman.2024.08.030">doi</a></li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Social Disadvantage Indices</span>
    <span class="project-badge">Published</span>
    <span class="project-tags">[Health Policy]</span>
  </div>
  <div class="project-description">
    These projects explored the application of social disadvantage indices, which are measurements that aggregate various socioeconomic factors associated with a region. These indices have been found to associate strongly with health outcomes, and are thus often used in health policy. My work here questions whether these indices can be used interchangeably.
  </div>
  <div class="publications-list">
    <ul>
      <li>Zolotor, A., <strong>Huang, R. W.</strong>, Bhavsar, N. A., & Cholera, R. (2024). <em>Pediatrics</em>. <a href="https://doi.org/10.1542/peds.2023-064463">doi</a></li>
      <li><strong>Huang, R. W.</strong>, Zolotor, A. F., et al. (2024). <em>AcademyHealth Research Meeting</em>.</li>
    </ul>
  </div>
</div>

</div>

<div class="theme-box">

<h3>Economics of Innovation</h3>

<div class="section-narrative">
I'm interested in the factors necessary to promote innovation and how we can measure the utility of the marginal idea.
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Financing Pharmaceutical Innovation for Low-Income Countries</span>
    <span class="project-badge">Published</span>
    <span class="project-tags">[Health Policy]</span>
  </div>
  <div class="project-description">
    These projects explored how to promote pharmaceutical innovation for diseases that primarily burden low-income countries, where the traditional economic incentives for R&D don't exist. While doing this work, I focused on how institutional systems, such as public-private development partnerships and international aid, coordinated research efforts and shaped the priorities of drug development in these settings.
  </div>
  <div class="publications-list">
    <ul>
      <li>McDade, K. K., Mao, W., Prizzon, A., <strong>Huang, R. W.</strong>, & Ogbuoji, O. (2023). <em>Front Public Health</em> 11. <a href="https://doi.org/10.3389/fpubh.2023.1096224">doi</a></li>
      <li><strong>Huang, R. W.</strong>, McDade, K. K., Yamey, G., & Mao, W. (2022). <em>CUGH Conference</em>.</li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Early Claims and M&A Behavior Following the IRA</span>
    <span class="project-badge">Published</span>
    <span class="project-tags">[Health Policy]</span>
  </div>
  <div class="project-description">
    I co-authored this blog with Richard Frank during my summer internship at the Brookings Institution. Many pharmaceutical companies claimed that the Inflation Reduction Act (IRA) would reduce pharmaceutical innovation. This blog challenges this claim by observing that M&A activity in the pharmaceutical industry has shown little sign of disruption since the IRA was enacted.
  </div>
  <div class="publications-list">
    <ul>
      <li>Frank, R. G. & <strong>Huang, R. W.</strong> (2023). "Early claims and M&A behavior following enactment of the drug provisions in the IRA." <em>Brookings Institution</em>. <a href="https://www.brookings.edu/articles/early-claims-and-ma-behavior-following-enactment-of-the-drug-provisions-in-the-ira/">link</a></li>
    </ul>
  </div>
</div>

</div>

<div class="theme-box">

<h3>Miscellaneous</h3>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Development of Lateral Pulvinar Resting State Functional Connectivity and Its Role in Attention</span>
    <span class="project-badge">Published</span>
    <span class="project-tags">[Neuroscience]</span>
  </div>
  <div class="publications-list">
    <ul>
      <li><strong>Huang, R. W.</strong> & Barber, A. D. (2021). <em>Cortex</em> 136. <a href="https://doi.org/10.1016/j.cortex.2020.12.004">doi</a></li>
    </ul>
  </div>
</div>

<div class="project-card">
  <div class="project-header">
    <span class="project-title">Research Gaps for Addressing the Social Determinants of Health: A Literature Matrix Analysis on Systematic Reviews</span>
    <span class="project-badge">Published</span>
    <span class="project-tags">[Health Policy]</span>
  </div>
  <div class="publications-list">
    <ul>
      <li><strong>Huang, R. W.</strong>*, Fang, Y.*, et al. (2022). <em>HSR Conference, Bogota</em>.</li>
    </ul>
  </div>
</div>

</div>
