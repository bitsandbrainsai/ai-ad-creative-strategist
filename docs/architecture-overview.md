<h1>Architecture Overview</h1>

<h2>1. System Overview</h2>
<p>
The <strong>AI Ad Creative Strategist (Foreplay + SORA)</strong> is a fully automated, agentic workflow
designed to operationalize competitive advertising intelligence into AI-generated video creatives.
The system continuously discovers high-performing competitor ads, analyzes their creative structure,
adapts proven strategies to a target brand, and generates new video ads using advanced multimodal AI models.
</p>

<p>
The architecture is implemented as a single orchestrated workflow using a workflow automation engine.
All stages are executed deterministically in sequence, with controlled looping, filtering, persistence,
and human-in-the-loop notification points.
</p>

<hr />

<h2>2. Architectural Design Principles</h2>
<ul>
  <li><strong>Automation-first:</strong> No manual intervention required for discovery, analysis, or generation.</li>
  <li><strong>Data-driven creativity:</strong> Creative generation is grounded in empirically validated ad performance.</li>
  <li><strong>Phase-based orchestration:</strong> Clear separation of concerns across logical workflow phases.</li>
  <li><strong>Vendor-agnostic abstraction:</strong> External services are treated as interchangeable providers.</li>
  <li><strong>Auditability:</strong> All inputs, outputs, and decisions are persisted for traceability.</li>
  <li><strong>Security by design:</strong> Credentials and secrets are externalized and never hard-coded.</li>
</ul>

<hr />

<h2>3. High-Level Architecture Diagram</h2>
<p>
The system follows a linear–iterative pipeline architecture with feedback loops for batch processing.
Each execution cycle processes multiple ads independently while maintaining a unified orchestration context.
</p>

<p><em>(Refer to diagrams in <code>assets/diagrams/</code> for visual representations of each stage.)</em></p>

<hr />

<h2>4. Core Architectural Components</h2>

<h3>4.1 Orchestration Layer</h3>
<ul>
  <li>Responsible for sequencing, branching, looping, and failure handling</li>
  <li>Defines execution order and dependency resolution</li>
  <li>Controls batch size and execution boundaries</li>
</ul>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Component</th>
    <th>Responsibility</th>
  </tr>
  <tr>
    <td>Scheduled Trigger</td>
    <td>Initiates daily workflow execution</td>
  </tr>
  <tr>
    <td>Loop Controller</td>
    <td>Iterates over qualified ads in a controlled manner</td>
  </tr>
  <tr>
    <td>Filter Nodes</td>
    <td>Enforce qualification and gating rules</td>
  </tr>
</table>

<hr />

<h3>4.2 External Intelligence Ingestion Layer</h3>
<p>
This layer is responsible for discovering and ingesting competitor advertising data from external
ad intelligence platforms.
</p>

<ul>
  <li>Fetches live competitor ads</li>
  <li>Restricts ingestion to specific formats (video)</li>
  <li>Orders ads by longevity to infer performance</li>
</ul>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Input</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Brand Identifier</td>
    <td>Unique identifier for competitor brand</td>
  </tr>
  <tr>
    <td>Runtime Metadata</td>
    <td>Used to infer ad performance longevity</td>
  </tr>
  <tr>
    <td>Media URLs</td>
    <td>Video assets for downstream analysis</td>
  </tr>
</table>

<hr />

<h3>4.3 Qualification & Selection Layer</h3>
<p>
Not all ads are suitable for analysis. This layer applies deterministic qualification rules
to isolate statistically meaningful ads.
</p>

<ol>
  <li>Evaluate ad runtime duration</li>
  <li>Exclude ads below minimum runtime threshold</li>
  <li>Exclude ads exceeding freshness threshold</li>
  <li>Forward only “proven but current” ads</li>
</ol>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Rule</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td>Runtime &gt; 30 days</td>
    <td>Ensures performance validation</td>
  </tr>
  <tr>
    <td>Runtime &lt; 60 days</td>
    <td>Avoids creative fatigue bias</td>
  </tr>
</table>

<hr />

<h3>4.4 Creative Intelligence Extraction Layer</h3>
<p>
This layer converts raw video ads into structured creative intelligence.
It transforms unstructured multimedia into actionable strategic insights.
</p>

<ul>
  <li>Transcript aggregation and normalization</li>
  <li>Second-by-second visual analysis</li>
  <li>Extraction of hooks, pacing, messaging, and CTA logic</li>
</ul>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Output Artifact</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Chronological Breakdown</td>
    <td>Scene-level narrative of the ad</td>
  </tr>
  <tr>
    <td>Messaging Analysis</td>
    <td>Value propositions and emotional triggers</td>
  </tr>
  <tr>
    <td>Structural Blueprint</td>
    <td>Reusable creative framework</td>
  </tr>
</table>

<hr />

<h3>4.5 Brand Context & Adaptation Layer</h3>
<p>
This layer merges competitive intelligence with brand-specific constraints and identity.
It ensures generated creatives are on-brand while preserving proven performance structures.
</p>

<ul>
  <li>Brand positioning and voice ingestion</li>
  <li>Visual identity and color system alignment</li>
  <li>Value proposition substitution</li>
</ul>

<p>
A dedicated agent synthesizes:
</p>
<ul>
  <li>Winning ad structure (from analysis)</li>
  <li>Target brand context (from internal datastore)</li>
</ul>

<p>
The output is a fully specified, AI-optimized video generation prompt.
</p>

<hr />

<h3>4.6 Generative Media Layer</h3>
<p>
This layer is responsible for converting structured prompts into final video assets.
</p>

<ol>
  <li>Receive consolidated video generation prompt</li>
  <li>Invoke multimodal video generation model</li>
  <li>Produce cinematic, scene-accurate video output</li>
</ol>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Aspect</th>
    <th>Specification</th>
  </tr>
  <tr>
    <td>Input</td>
    <td>Structured, scene-by-scene prompt</td>
  </tr>
  <tr>
    <td>Output</td>
    <td>High-quality video creative</td>
  </tr>
  <tr>
    <td>Control</td>
    <td>Deterministic scene ordering and branding</td>
  </tr>
</table>

<hr />

<h3>4.7 Persistence & Audit Layer</h3>
<p>
All significant artifacts are persisted to ensure traceability, reuse, and analysis.
</p>

<ul>
  <li>Winning competitor ads</li>
  <li>Creative intelligence outputs</li>
  <li>Generated prompts</li>
  <li>Generated media metadata</li>
</ul>

<p>
This layer enables:
</p>
<ul>
  <li>Historical analysis</li>
  <li>Creative iteration tracking</li>
  <li>Compliance and audit readiness</li>
</ul>

<hr />

<h3>4.8 Notification & Human Oversight Layer</h3>
<p>
The system incorporates explicit human-in-the-loop checkpoints.
Generated creatives are never auto-launched.
</p>

<ul>
  <li>Automated team notifications</li>
  <li>Clear indication of creative readiness</li>
  <li>Manual review and activation workflow</li>
</ul>

<hr />

<h2>5. End-to-End Execution Flow Summary</h2>

<ol>
  <li>Daily trigger initiates workflow</li>
  <li>Competitor ads are fetched and normalized</li>
  <li>Ads are filtered for performance qualification</li>
  <li>Qualified ads are processed in batches</li>
  <li>Creative intelligence is extracted from videos</li>
  <li>Brand context is merged with winning structures</li>
  <li>New video creatives are generated</li>
  <li>Artifacts are logged and team is notified</li>
</ol>

<hr />

<h2>6. Architectural Boundaries & Non-Goals</h2>
<ul>
  <li>Does not perform media buying or budget optimization</li>
  <li>Does not auto-publish ads without review</li>
  <li>Does not store credentials in source control</li>
</ul>

<hr />

<h2>7. Architectural Extensibility</h2>
<p>
The architecture is intentionally extensible. Future enhancements may include:
</p>
<ul>
  <li>Multi-brand parallel execution</li>
  <li>Creative performance feedback loops</li>
  <li>Multi-platform ad adaptation</li>
  <li>CI/CD-style creative experimentation</li>
</ul>

<hr />

<h2>8. Conclusion</h2>
<p>
This architecture represents a modern, production-grade implementation of agentic AI for marketing operations.
It transforms competitive intelligence into repeatable creative output, reducing manual effort while increasing
creative quality, speed, and consistency.
</p>

</body>
</html>
