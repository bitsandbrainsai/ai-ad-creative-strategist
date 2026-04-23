<div align="center">
  <img 
    src="assets/diagrams/AI Ad Creative Strategist.png" 
    alt="AI Ad Creative Strategist Logo Animation"
    width="100%"
  />

  <h1 style="font-size: 3em; font-weight: 800; margin: 0.4em 0 0;">
    AI Ad Creative Strategist 
  </h1>

  <h3 style="margin-top: 0.6em;">
    Agentic AI for Ad Intelligence, Strategy, and Video Generation  
  </h3>

  <p>
    <em>A next-generation, enterprise-grade AI system that transforms fragmented competitor ad data into high-performance, brand-safe video creatives through a fully orchestrated, agentic pipeline. </em>
  </p>
</div>

<hr />

<h1>🧾 Executive Summary</h1>
<p>
AI Ad Creative Strategist is an enterprise-grade, agentic AI system that automates
the full lifecycle of high-performance advertising creative generation.
The platform continuously monitors competitor ads, identifies winning creatives,
extracts creative intelligence, adapts strategies to a target brand, and generates
new AI-powered video advertisements using advanced multimodal models.
</p>

<p>
The solution replaces manual ad research, creative strategy formulation, and initial
video production with a deterministic, auditable, and scalable workflow.
</p>

<hr />

<h1>📑 Table of Contents</h1>
<ol>
  <li>🧩 Project Overview</li>
  <li>🎯 Objectives & Goals</li>
  <li>✅ Acceptance Criteria</li>
  <li>💻 Prerequisites</li>
  <li>⚙️ Installation & Setup</li>
  <li>🔗 API Documentation</li>
  <li>🖥️ UI / Frontend</li>
  <li>🔢 Status Codes</li>
  <li>🚀 Features</li>
  <li>🧱 Tech Stack & Architecture</li>
  <li>🛠️ Workflow & Implementation</li>
  <li>🧪 Testing & Validation</li>
  <li>🔍 Validation Summary</li>
  <li>🧰 Verification Testing Tools</li>
  <li>🧯 Troubleshooting & Debugging</li>
  <li>🔒 Security & Secrets</li>
  <li>☁️ Deployment</li>
  <li>⚡ Quick-Start Cheat Sheet</li>
  <li>🧾 Usage Notes</li>
  <li>🧠 Performance & Optimization</li>
  <li>🌟 Enhancements & Features</li>
  <li>🧩 Maintenance & Future Work</li>
  <li>🏆 Key Achievements</li>
  <li>🧮 High-Level Architecture</li>
  <li>🗂️ Project Structure</li>
  <li>🧭 How to Demonstrate Live</li>
  <li>💡 Summary, Closure & Compliance</li>
</ol>

<hr />

<h1>🧩 Project Overview</h1>
<p>
This project implements a five-phase AI advertising pipeline orchestrated through
a workflow automation engine. It integrates external ad intelligence APIs, multiple
AI models, persistent data storage, and human-in-the-loop controls.
</p>

<p>
The system is designed to be:
</p>
<ul>
  <li>Fully automated yet review-gated</li>
  <li>Data-driven and repeatable</li>
  <li>Scalable across brands and markets</li>
  <li>Auditable and compliant</li>
</ul>

<hr />

<h1>🎯 Objectives & Goals</h1>
<ul>
  <li>Automate competitor ad discovery</li>
  <li>Identify statistically winning creatives</li>
  <li>Extract reusable creative intelligence</li>
  <li>Adapt strategies to a new brand identity</li>
  <li>Generate production-ready AI video ads</li>
  <li>Reduce time-to-creative from weeks to minutes</li>
</ul>

<hr />

<h1>✅ Acceptance Criteria</h1>
<ul>
  <li>Workflow runs end-to-end without manual intervention</li>
  <li>Only qualified ads are processed</li>
  <li>Generated creatives are brand-aligned</li>
  <li>All outputs are logged and traceable</li>
  <li>No secrets are committed to source control</li>
</ul>

<hr />

<h1>💻 Prerequisites</h1>
<ul>
  <li>Node-based workflow orchestration platform</li>
  <li>API access to ad intelligence provider</li>
  <li>Access to multimodal AI models</li>
  <li>Persistent datastore (Airtable)</li>
  <li>Team communication platform (Slack)</li>
</ul>

<hr />

<h1>⚙️ Installation & Setup</h1>
<ol>
  <li>Clone the repository</li>
  <li>Configure environment variables</li>
  <li>Import workflow JSON</li>
  <li>Bind credentials</li>
  <li>Populate brand data</li>
  <li>Enable scheduled trigger</li>
</ol>

<hr />

<h1>🔗 API Documentation</h1>

<p>
The AI Ad Creative Strategist integrates with multiple external APIs to enable
end-to-end creative intelligence, adaptation, and generation. Each API plays a
distinct role in the pipeline and is invoked at a specific phase of execution.
</p>

<h2>Integrated APIs Overview</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>API / Service</th>
    <th>Phase Used</th>
    <th>Purpose</th>
    <th>Data In</th>
    <th>Data Out</th>
  </tr>
  <tr>
    <td>Foreplay Public API</td>
    <td>Phase 1</td>
    <td>Competitor ad discovery</td>
    <td>Brand ID, filters</td>
    <td>Ad metadata, video URLs</td>
  </tr>
  <tr>
    <td>Gemini Multimodal API</td>
    <td>Phase 3</td>
    <td>Creative intelligence extraction</td>
    <td>Video URL, transcript</td>
    <td>Scene analysis, hooks, CTA logic</td>
  </tr>
  <tr>
    <td>Anthropic Claude API</td>
    <td>Phase 4</td>
    <td>Brand strategy adaptation</td>
    <td>Creative blueprint, brand data</td>
    <td>SORA-optimized prompt</td>
  </tr>
  <tr>
    <td>SORA 2 Video API</td>
    <td>Phase 5</td>
    <td>Video ad generation</td>
    <td>Structured prompt</td>
    <td>Generated video asset</td>
  </tr>
  <tr>
    <td>Slack Webhook API</td>
    <td>Phase 5</td>
    <td>Team notification</td>
    <td>Status payload</td>
    <td>Message delivery</td>
  </tr>
</table>

<h2>API Invocation Characteristics</h2>
<ul>
  <li>All API calls are synchronous within their execution phase</li>
  <li>Rate limiting is controlled via loop iteration boundaries</li>
  <li>Failures are isolated per ad item</li>
  <li>Retries are delegated to workflow-level controls</li>
</ul>

<hr />

<h1>🖥️ UI / Frontend</h1>
<p>
This project is backend-first. The UI consists of:
</p>
<ul>
  <li>Workflow visualization canvas</li>
  <li>Airtable dashboards</li>
  <li>Slack notifications</li>
</ul>

<p>
Styling changes are managed at the brand data level rather than UI code.
</p>

<hr />

<h1>🔢 Status Codes</h1>
<table border="1" cellpadding="6">
<tr><th>Code</th><th>Meaning</th></tr>
<tr><td>200</td><td>Successful execution</td></tr>
<tr><td>400</td><td>Invalid input or configuration</td></tr>
<tr><td>401</td><td>Authentication failure</td></tr>
<tr><td>500</td><td>External service failure</td></tr>
</table>

<hr />

<h1>🚀 Features</h1>

<p>
The platform delivers a comprehensive feature set designed for modern
performance marketing, creative operations, and AI-driven growth teams.
</p>

<h2>Core Functional Features</h2>
<ul>
  <li>Automated competitor ad ingestion with zero manual research</li>
  <li>Runtime-based qualification to identify proven winning creatives</li>
  <li>Second-by-second video and narrative intelligence extraction</li>
  <li>Brand-safe creative strategy adaptation using AI agents</li>
  <li>Automated cinematic video generation using structured prompts</li>
</ul>

<h2>Operational & Enterprise Features</h2>
<ul>
  <li>Full audit trail of inputs, transformations, and outputs</li>
  <li>Human-in-the-loop approval workflow</li>
  <li>Failure isolation and graceful degradation</li>
  <li>Cost control via deterministic filtering</li>
  <li>Extensible phase-based architecture</li>
</ul>

<h2>Business Impact Features</h2>
<ul>
  <li>Reduced creative ideation time from weeks to minutes</li>
  <li>Consistent creative quality across campaigns</li>
  <li>Scalable multi-brand execution</li>
  <li>Repeatable creative experimentation</li>
</ul>

<hr />

<h1>🧱 Tech Stack & Architecture</h1>

<h2>Technology Stack</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Layer</th>
    <th>Technology</th>
    <th>Role</th>
  </tr>
  <tr>
    <td>Orchestration</td>
    <td>n8n</td>
    <td>Workflow automation and control</td>
  </tr>
  <tr>
    <td>Ad Intelligence</td>
    <td>Foreplay API</td>
    <td>Competitor ad discovery</td>
  </tr>
  <tr>
    <td>Analysis AI</td>
    <td>Gemini</td>
    <td>Multimodal creative analysis</td>
  </tr>
  <tr>
    <td>Strategy AI</td>
    <td>Claude</td>
    <td>Brand adaptation and reasoning</td>
  </tr>
  <tr>
    <td>Generation AI</td>
    <td>SORA 2</td>
    <td>Video ad generation</td>
  </tr>
  <tr>
    <td>Persistence</td>
    <td>Airtable</td>
    <td>Audit logs and brand data</td>
  </tr>
  <tr>
    <td>Notification</td>
    <td>Slack</td>
    <td>Human review signaling</td>
  </tr>
</table>

<h2>ASCII Component Diagram</h2>

<pre>
[ Daily Scheduler ]
        |
        v
[ Foreplay API ]
        |
        v
[ Qualification Filter ]
        |
        v
[ Loop Controller ]
        |
        v
[ Gemini Analysis ]
        |
        v
[ Claude Adaptation ]
        |
        v
[ SORA 2 Generator ]
        |
        v
[ Airtable Logs ] ---> [ Slack Notifications ]
</pre>

<hr />

<h1>🛠️ Workflow & Implementation</h1>

<h2>Step-by-Step Execution Flow</h2>

<ol>
  <li>Scheduled trigger initiates a new execution context</li>
  <li>Competitor ads are fetched from the ad intelligence API</li>
  <li>Ad metadata is normalized and prepared for evaluation</li>
  <li>Ads are filtered using runtime qualification rules</li>
  <li>Each qualified ad enters a controlled processing loop</li>
  <li>Video transcripts are aggregated and cleaned</li>
  <li>Multimodal AI analyzes creative structure and messaging</li>
  <li>Creative intelligence is persisted for traceability</li>
  <li>Brand context is loaded from internal datastore</li>
  <li>AI agent adapts winning strategy to brand constraints</li>
  <li>Structured video generation prompt is produced</li>
  <li>Video creative is generated using SORA 2</li>
  <li>Outputs are logged and notifications are dispatched</li>
</ol>

<h2>Failure Handling</h2>
<ul>
  <li>Errors are scoped to individual ads</li>
  <li>Workflow continues processing remaining items</li>
  <li>Execution logs capture error context</li>
</ul>

<hr />

<h1>🧪 Testing & Validation</h1>
<table border="1" cellpadding="6">
<tr><th>ID</th><th>Area</th><th>Command</th><th>Expected Output</th><th>Explanation</th></tr>
<tr><td>T-01</td><td>Ingestion</td><td>Manual run</td><td>Ads fetched</td><td>Validates API access</td></tr>
<tr><td>T-02</td><td>Filtering</td><td>Manual run</td><td>Qualified ads only</td><td>Ensures logic correctness</td></tr>
</table>

<hr />

<h1>🔍 Validation Summary</h1>
<p>
All workflow phases were validated through controlled manual executions
and persisted data inspection.
</p>

<hr />

<h1>🧰 Verification Testing Tools & Command Examples</h1>
<ul>
  <li>Workflow execution logs</li>
  <li>Airtable record inspection</li>
  <li>Slack message verification</li>
</ul>

<hr />

<h1>🧯 Troubleshooting & Debugging</h1>

<h2>Common Issues and Resolutions</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Issue</th>
    <th>Likely Cause</th>
    <th>Resolution</th>
  </tr>
  <tr>
    <td>No ads fetched</td>
    <td>API credentials invalid</td>
    <td>Verify API token and permissions</td>
  </tr>
  <tr>
    <td>No winning ads</td>
    <td>Strict runtime filters</td>
    <td>Adjust qualification thresholds</td>
  </tr>
  <tr>
    <td>Off-brand output</td>
    <td>Incomplete brand data</td>
    <td>Review brand context records</td>
  </tr>
  <tr>
    <td>High cost execution</td>
    <td>Too many qualified ads</td>
    <td>Reduce loop batch size</td>
  </tr>
</table>

<h2>Debugging Best Practices</h2>
<ul>
  <li>Inspect node-level execution logs</li>
  <li>Validate intermediate data objects</li>
  <li>Re-run workflow with a single ad</li>
</ul>

<hr />

<h1>🔒 Security & Secrets</h1>
<ul>
  <li>All secrets stored externally</li>
  <li>.env.example provided</li>
  <li>No credentials in repository</li>
</ul>

<hr />

<h1>☁️ Deployment</h1>

<p>
The project is designed for backend execution, while documentation and dashboards
can be deployed using modern frontend hosting platforms.
</p>

<h2>Deployment Targets</h2>
<ul>
  <li>Workflow Engine: Self-hosted or managed</li>
  <li>Documentation: Vercel (static deployment)</li>
</ul>

<h2>Deployment Characteristics</h2>
<ul>
  <li>Stateless execution model</li>
  <li>No runtime frontend dependency</li>
  <li>Separation of compute and presentation</li>
</ul>

<hr />

<h1>⚡ Quick-Start Cheat Sheet</h1>
<ul>
  <li>Import workflow</li>
  <li>Bind credentials</li>
  <li>Enable trigger</li>
  <li>Review Slack output</li>
</ul>

<hr />

<h1>🧾 Usage Notes</h1>
<ul>
  <li>Generated ads are paused by default</li>
  <li>Human review is mandatory</li>
</ul>

<hr />

<h1>🧠 Performance & Optimization</h1>
<ul>
  <li>Batch processing reduces cost</li>
  <li>Filtering minimizes AI usage</li>
  <li>Stateless execution ensures scalability</li>
</ul>

<hr />

<h1>🌟 Enhancements & Features</h1>
<ul>
  <li>Multi-brand parallel execution</li>
  <li>Creative A/B feedback loop</li>
  <li>Auto-scoring creatives</li>
</ul>

<hr />

<h1>🧩 Maintenance & Future Work</h1>
<ul>
  <li>Model upgrades</li>
  <li>New ad platforms</li>
  <li>Creative performance feedback</li>
</ul>

<hr />

<h1>🏆 Key Achievements</h1>
<ul>
  <li>End-to-end AI creative automation</li>
  <li>Brand-safe generative ads</li>
  <li>Production-ready architecture</li>
</ul>

<hr />

<h1>🧮 High-Level Architecture</h1>

<pre>
[ Time Trigger ]
       |
       v
[ Competitor Ad Source ]
       |
       v
[ Qualification Layer ]
       |
       v
[ Intelligence Extraction ]
       |
       v
[ Brand Strategy Layer ]
       |
       v
[ Creative Generation ]
       |
       v
[ Audit & Notification ]
</pre>

<hr />

<h1>🗂️ Project Structure</h1>
<pre>
AI-AD-CREATIVE-STRATEGIST/
├── assets/
│   └── diagrams/
│       ├── 01-workflow-trigger-and-ad-ingestion.png
│       ├── 02-winning-ad-filtering-and-analysis.png
│       ├── 03-brand-adaptation-and-prompt-generation.png
│       └── 04-video-generation-and-delivery.png
├── docs/
│   ├── architecture-overview.md
│   ├── workflow-phases.md
│   ├── data-flow.md
│   └── setup-guide.md
├── workflows/
│   └── ai-ad-creative-strategist.json
├── .env.example
├── .gitignore
└── README.md
</pre>

<hr />

<h1>🧭 How to Demonstrate Live</h1>
<ol>
  <li>Open workflow canvas</li>
  <li>Run manual execution</li>
  <li>Show Airtable records</li>
  <li>Show Slack notification</li>
</ol>

<hr />

<h1>💡 Summary, Closure & Compliance</h1>

<p>
The AI Ad Creative Strategist represents a compliant, auditable, and production-ready
implementation of agentic AI for marketing operations.
</p>

<h2>Compliance Alignment</h2>
<ul>
  <li>Separation of secrets from code</li>
  <li>Human approval gates</li>
  <li>Deterministic execution paths</li>
  <li>Complete audit trails</li>
</ul>

<h2>Closure Statement</h2>
<p>
This system demonstrates how modern AI can be operationalized responsibly to
augment creative teams, reduce costs, and improve advertising effectiveness
without compromising governance or control.
</p>

</body>
</html>
