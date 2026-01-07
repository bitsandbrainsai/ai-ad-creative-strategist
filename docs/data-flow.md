<h1>Data Flow</h1>

<p>
This document describes the complete end-to-end data flow for the
<strong>AI Ad Creative Strategist</strong> workflow. It details how data is
ingested, transformed, enriched, persisted, and emitted across each phase
of the workflow.
</p>

<p>
The focus of this document is on:
</p>
<ul>
  <li>Data sources and sinks</li>
  <li>Intermediate data structures</li>
  <li>Transformation logic</li>
  <li>State propagation between phases</li>
</ul>

<hr />

<h2>1. Data Flow Principles</h2>

<ul>
  <li>All data flows are unidirectional within a single execution context</li>
  <li>Each phase consumes only the outputs of prior phases</li>
  <li>Raw external data is never passed downstream without normalization</li>
  <li>Derived intelligence artifacts are persisted for auditability</li>
  <li>No credentials or secrets are embedded in data payloads</li>
</ul>

<hr />

<h2>2. High-Level Data Flow Overview</h2>

<p>
The workflow processes data through five major stages, transforming it
from raw external inputs into structured creative outputs.
</p>

<ol>
  <li>External competitor ad ingestion</li>
  <li>Qualification and reduction</li>
  <li>Creative intelligence extraction</li>
  <li>Brand-contextual adaptation</li>
  <li>Creative generation and notification</li>
</ol>

<p><em>
(Refer to architecture diagrams in <code>assets/diagrams/</code> for visual flow representations.)
</em></p>

<hr />

<h2>3. Data Sources</h2>

<h3>3.1 External Data Sources</h3>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Source</th>
    <th>Data Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Competitor Ad Intelligence API</td>
    <td>JSON</td>
    <td>Live competitor ad metadata and media references</td>
  </tr>
  <tr>
    <td>Video Analysis Model</td>
    <td>Multimodal Output</td>
    <td>Visual and narrative analysis of ad videos</td>
  </tr>
  <tr>
    <td>Generative Language Model</td>
    <td>Text</td>
    <td>Creative adaptation and prompt synthesis</td>
  </tr>
  <tr>
    <td>Video Generation Model</td>
    <td>Media Metadata</td>
    <td>Generated video creative artifacts</td>
  </tr>
</table>

<h3>3.2 Internal Data Sources</h3>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Source</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td>Brand Context Datastore</td>
    <td>Provides brand identity, messaging, and visual constraints</td>
  </tr>
  <tr>
    <td>Winning Ads Datastore</td>
    <td>Historical persistence of qualified competitor ads</td>
  </tr>
</table>

<hr />

<h2>4. Phase-by-Phase Data Flow</h2>

<h2>4.1 Phase 1 – Competitor Ad Ingestion</h2>

<h3>Input Data</h3>
<ul>
  <li>Brand identifier</li>
  <li>Query parameters (format, language, live status)</li>
</ul>

<h3>Raw Output</h3>
<ul>
  <li>Array of competitor ad objects</li>
  <li>Nested metadata including runtime, platform, and media URLs</li>
</ul>

<h3>Transformation Steps</h3>
<ol>
  <li>Receive raw API JSON response</li>
  <li>Extract relevant ad records</li>
  <li>Discard non-video and non-live ads</li>
  <li>Flatten nested metadata fields</li>
</ol>

<h3>Normalized Output</h3>
<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>ad_id</td>
    <td>Unique advertisement identifier</td>
  </tr>
  <tr>
    <td>brand_id</td>
    <td>Competitor brand identifier</td>
  </tr>
  <tr>
    <td>runtime_days</td>
    <td>Ad longevity metric</td>
  </tr>
  <tr>
    <td>video_url</td>
    <td>Primary media reference</td>
  </tr>
</table>

<hr />

<h2>4.2 Phase 2 – Qualification and Reduction</h2>

<h3>Input Data</h3>
<ul>
  <li>Normalized competitor ad records</li>
</ul>

<h3>Filtering Logic</h3>
<ol>
  <li>Evaluate runtime_days field</li>
  <li>Apply lower and upper threshold constraints</li>
  <li>Remove non-qualifying records</li>
</ol>

<h3>Intermediate Output</h3>
<ul>
  <li>Reduced set of “winning” ads</li>
  <li>Each record isolated for independent processing</li>
</ul>

<h3>Persistence Output</h3>
<p>
Qualified ads are written to persistent storage with the following attributes:
</p>

<ul>
  <li>Ad identifiers</li>
  <li>Media references</li>
  <li>Qualification timestamp</li>
  <li>Platform metadata</li>
</ul>

<hr />

<h2>4.3 Phase 3 – Creative Intelligence Extraction</h2>

<h3>Input Data</h3>
<ul>
  <li>Winning ad media URL</li>
  <li>Associated ad metadata</li>
</ul>

<h3>Transcript Aggregation</h3>
<ol>
  <li>Receive segmented transcript data</li>
  <li>Concatenate sentence fragments</li>
  <li>Normalize punctuation and spacing</li>
</ol>

<h3>Video Intelligence Extraction</h3>
<p>
The video analysis model produces structured narrative and visual insights.
</p>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Output Component</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Scene Timeline</td>
    <td>Ordered sequence of visual events</td>
  </tr>
  <tr>
    <td>Hook Analysis</td>
    <td>Identification of attention-grabbing moments</td>
  </tr>
  <tr>
    <td>Messaging Layers</td>
    <td>Value propositions and emotional triggers</td>
  </tr>
</table>

<h3>Derived Data Artifact</h3>
<p>
The result is a fully textual, structured creative intelligence document that
abstracts away the original media.
</p>

<hr />

<h2>4.4 Phase 4 – Brand Contextual Adaptation</h2>

<h3>Input Data</h3>
<ul>
  <li>Creative intelligence artifact (Phase 3)</li>
  <li>Brand context dataset</li>
</ul>

<h3>Brand Context Fields</h3>
<ul>
  <li>Brand voice and tone</li>
  <li>Core value propositions</li>
  <li>Visual identity constraints</li>
  <li>Product-specific messaging rules</li>
</ul>

<h3>Transformation Process</h3>
<ol>
  <li>Map competitor value propositions to brand equivalents</li>
  <li>Adapt language to brand tone constraints</li>
  <li>Replace visual identity references</li>
  <li>Preserve original structural sequencing</li>
</ol>

<h3>Output Artifact</h3>
<p>
A consolidated, scene-by-scene video generation prompt optimized for
machine interpretation.
</p>

<hr />

<h2>4.5 Phase 5 – Creative Generation and Emission</h2>

<h3>Input Data</h3>
<ul>
  <li>Structured video generation prompt</li>
</ul>

<h3>Generation Output</h3>
<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Artifact</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Video Asset</td>
    <td>Generated ad creative</td>
  </tr>
  <tr>
    <td>Generation Metadata</td>
    <td>Prompt reference, timestamps, identifiers</td>
  </tr>
</table>

<h3>Persistence and Notification</h3>
<ul>
  <li>Store generation metadata in datastore</li>
  <li>Associate creative with source winning ad</li>
  <li>Emit notification payload to team channel</li>
</ul>

<hr />

<h2>5. Data Lineage Summary</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Stage</th>
    <th>Input</th>
    <th>Output</th>
  </tr>
  <tr>
    <td>Ingestion</td>
    <td>Raw competitor ads</td>
    <td>Normalized ad records</td>
  </tr>
  <tr>
    <td>Qualification</td>
    <td>Normalized ads</td>
    <td>Winning ads</td>
  </tr>
  <tr>
    <td>Intelligence</td>
    <td>Winning ads</td>
    <td>Creative blueprint</td>
  </tr>
  <tr>
    <td>Adaptation</td>
    <td>Blueprint + brand data</td>
    <td>Generation prompt</td>
  </tr>
  <tr>
    <td>Generation</td>
    <td>Prompt</td>
    <td>Video creative</td>
  </tr>
</table>

<hr />

<h2>6. Conclusion</h2>

<p>
The data flow architecture ensures that every creative output is fully traceable
back to its source inputs and transformations. Each phase incrementally enriches
the data, converting unstructured external signals into deterministic, brand-safe,
AI-generated advertising assets.
</p>

</body>
</html>
