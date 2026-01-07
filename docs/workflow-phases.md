<h1>Workflow Phases</h1>

<p>
This document provides a detailed, phase-by-phase technical breakdown of the
<strong>AI Ad Creative Strategist</strong> workflow. Each phase corresponds to a
distinct logical responsibility within a single orchestrated execution pipeline.
</p>

<p>
All phases execute sequentially within one workflow run, with controlled looping
and persistence boundaries. No phase is independently deployable; together they
form a cohesive, deterministic automation system.
</p>

<hr />

<h2>Phase 1 – Trigger &amp; Competitor Discovery</h2>

<h3>1.1 Purpose</h3>
<p>
The purpose of Phase 1 is to automatically initiate the workflow on a fixed schedule
and ingest live competitor advertising data from an external ad intelligence provider.
This phase establishes the raw input dataset for all downstream processing.
</p>

<h3>1.2 Trigger Mechanism</h3>
<ul>
  <li>Execution is initiated by a scheduled trigger configured at a daily interval</li>
  <li>No manual invocation is required</li>
  <li>Each trigger creates a new, isolated execution context</li>
</ul>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Attribute</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>Trigger Type</td>
    <td>Time-based (scheduled)</td>
  </tr>
  <tr>
    <td>Frequency</td>
    <td>Once per day</td>
  </tr>
  <tr>
    <td>Execution Scope</td>
    <td>Single full workflow run</td>
  </tr>
</table>

<h3>1.3 Competitor Ad Ingestion</h3>
<p>
Upon trigger activation, the workflow issues a request to an external competitor
ad intelligence API to retrieve currently live advertisements for a specified brand.
</p>

<ul>
  <li>Only live ads are requested</li>
  <li>Results are limited to video-based creatives</li>
  <li>Ads are ordered by runtime duration</li>
</ul>

<h3>1.4 Metadata Normalization</h3>
<p>
The raw API response is normalized into a simplified internal structure to ensure
consistency and compatibility with downstream phases.
</p>

<ul>
  <li>Removal of non-essential API fields</li>
  <li>Standardization of runtime, media URLs, and identifiers</li>
  <li>Preparation of a flat list of ad records</li>
</ul>

<hr />

<h2>Phase 2 – Winning Ad Qualification</h2>

<h3>2.1 Purpose</h3>
<p>
Phase 2 filters the ingested competitor ads to identify creatives that are statistically
likely to be high-performing. Runtime longevity is used as a proxy signal for ad success.
</p>

<h3>2.2 Qualification Rules</h3>
<p>
Each ad is evaluated against deterministic runtime thresholds.
</p>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Rule</th>
    <th>Description</th>
    <th>Rationale</th>
  </tr>
  <tr>
    <td>Runtime &gt; 30 days</td>
    <td>Minimum performance validation</td>
    <td>Eliminates unproven or test ads</td>
  </tr>
  <tr>
    <td>Runtime &lt; 60 days</td>
    <td>Maximum freshness threshold</td>
    <td>Avoids creative fatigue bias</td>
  </tr>
</table>

<h3>2.3 Filtering Process</h3>
<ol>
  <li>Evaluate runtime metadata for each ad</li>
  <li>Discard ads failing qualification rules</li>
  <li>Retain only ads meeting both thresholds</li>
</ol>

<h3>2.4 Controlled Iteration</h3>
<p>
Qualified ads are processed using a controlled loop mechanism to ensure:
</p>
<ul>
  <li>Predictable execution order</li>
  <li>Isolation of failures to individual ads</li>
  <li>Cost and rate-limit control for downstream AI calls</li>
</ul>

<h3>2.5 Persistence of Qualified Ads</h3>
<p>
Metadata for each qualified ad is persisted to a datastore to establish a historical
record of identified “winning” creatives.
</p>

<ul>
  <li>Ad identifiers</li>
  <li>Brand and platform metadata</li>
  <li>Media URLs and thumbnails</li>
  <li>Qualification status</li>
</ul>

<hr />

<h2>Phase 3 – Creative Intelligence Extraction</h2>

<h3>3.1 Purpose</h3>
<p>
Phase 3 transforms qualified competitor ads from raw media into structured creative
intelligence. This phase is responsible for understanding <em>why</em> an ad works.
</p>

<h3>3.2 Transcript Extraction</h3>
<p>
Video transcript data is aggregated and normalized into a single coherent text stream.
</p>

<ul>
  <li>Segment-level transcripts are merged</li>
  <li>Sentence boundaries are normalized</li>
  <li>Noise and formatting artifacts are removed</li>
</ul>

<h3>3.3 Multimodal Video Analysis</h3>
<p>
Each video is analyzed using a multimodal AI model capable of interpreting both
visual and textual content.
</p>

<ol>
  <li>Scene-by-scene visual breakdown</li>
  <li>Temporal sequencing analysis</li>
  <li>Identification of hooks and attention triggers</li>
  <li>CTA placement and reinforcement analysis</li>
</ol>

<h3>3.4 Intelligence Outputs</h3>
<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Artifact</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Chronological Narrative</td>
    <td>Second-by-second breakdown of the ad</td>
  </tr>
  <tr>
    <td>Creative Strategy</td>
    <td>Underlying persuasion and messaging logic</td>
  </tr>
  <tr>
    <td>Structural Blueprint</td>
    <td>Reusable ad framework</td>
  </tr>
</table>

<p>
These outputs serve as the strategic foundation for brand adaptation.
</p>

<hr />

<h2>Phase 4 – Brand Adaptation</h2>

<h3>4.1 Purpose</h3>
<p>
Phase 4 adapts the extracted winning ad strategy to a target brand while preserving
the structural elements responsible for performance.
</p>

<h3>4.2 Brand Context Ingestion</h3>
<p>
Brand-specific data is loaded from an internal datastore.
</p>

<ul>
  <li>Brand positioning and value propositions</li>
  <li>Tone of voice and messaging constraints</li>
  <li>Visual identity and color guidelines</li>
  <li>Product-specific benefits</li>
</ul>

<h3>4.3 Strategy Adaptation</h3>
<p>
An AI agent synthesizes:
</p>
<ul>
  <li>Winning ad intelligence (Phase 3)</li>
  <li>Brand context constraints</li>
</ul>

<p>
The agent performs:
</p>
<ol>
  <li>Value proposition substitution</li>
  <li>Messaging alignment to brand voice</li>
  <li>Visual and tonal adaptation</li>
</ol>

<h3>4.4 Prompt Generation</h3>
<p>
The output of this phase is a fully specified, AI-optimized video generation prompt.
</p>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Prompt Component</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Scene Structure</td>
    <td>Chronological scene definitions</td>
  </tr>
  <tr>
    <td>Visual Direction</td>
    <td>Camera, lighting, and motion cues</td>
  </tr>
  <tr>
    <td>Brand Integration</td>
    <td>Logo, color, and identity placement</td>
  </tr>
</table>

<hr />

<h2>Phase 5 – Creative Generation &amp; Output</h2>

<h3>5.1 Purpose</h3>
<p>
Phase 5 converts the adapted strategy into a tangible video creative and prepares it
for human review and activation.
</p>

<h3>5.2 Video Generation</h3>
<ol>
  <li>Submit structured prompt to video generation model</li>
  <li>Generate cinematic, multi-scene video</li>
  <li>Ensure deterministic adherence to prompt structure</li>
</ol>

<h3>5.3 Persistence of Generated Creative</h3>
<p>
Generated outputs and metadata are logged for traceability.
</p>

<ul>
  <li>Prompt used</li>
  <li>Associated brand and source ad</li>
  <li>Generation timestamp</li>
</ul>

<h3>5.4 Notification &amp; Oversight</h3>
<p>
Upon successful generation:
</p>
<ul>
  <li>A notification is sent to the team</li>
  <li>The creative is marked as ready for review</li>
  <li>No automatic publishing occurs</li>
</ul>

<hr />

<h2>6. Phase Boundary Summary</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Phase</th>
    <th>Primary Responsibility</th>
    <th>Output</th>
  </tr>
  <tr>
    <td>Phase 1</td>
    <td>Input acquisition</td>
    <td>Normalized competitor ads</td>
  </tr>
  <tr>
    <td>Phase 2</td>
    <td>Qualification</td>
    <td>Winning ad set</td>
  </tr>
  <tr>
    <td>Phase 3</td>
    <td>Intelligence extraction</td>
    <td>Creative blueprint</td>
  </tr>
  <tr>
    <td>Phase 4</td>
    <td>Brand adaptation</td>
    <td>Video generation prompt</td>
  </tr>
  <tr>
    <td>Phase 5</td>
    <td>Execution &amp; delivery</td>
    <td>Ready-to-review video creative</td>
  </tr>
</table>

<hr />

<h2>7. Conclusion</h2>
<p>
The five phases together form a complete, production-grade creative automation
pipeline. Each phase is intentionally scoped, auditable, and deterministic, enabling
scalable, repeatable generation of high-quality advertising creatives.
</p>

</body>
</html>
