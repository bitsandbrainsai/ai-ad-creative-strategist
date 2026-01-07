<h1>Setup Guide</h1>

<p>
This document provides a comprehensive, step-by-step guide for deploying,
configuring, and operating the <strong>AI Ad Creative Strategist</strong> workflow.
It covers infrastructure prerequisites, credential configuration, workflow import,
environment setup, validation, and operational safeguards.
</p>

<hr />

<h2>1. Deployment Prerequisites</h2>

<h3>1.1 Infrastructure Requirements</h3>
<ul>
  <li>Running instance of a workflow automation platform (self-hosted or managed)</li>
  <li>Persistent storage enabled for workflow state and execution logs</li>
  <li>Outbound HTTPS access to external APIs</li>
  <li>Ability to securely store credentials and secrets</li>
</ul>

<h3>1.2 Account and Service Access</h3>
<p>
The following external services must be provisioned prior to setup:
</p>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Service Category</th>
    <th>Purpose</th>
    <th>Access Required</th>
  </tr>
  <tr>
    <td>Ad Intelligence Platform</td>
    <td>Competitor ad discovery</td>
    <td>API access token</td>
  </tr>
  <tr>
    <td>Multimodal Analysis Model</td>
    <td>Video and transcript analysis</td>
    <td>Model API credentials</td>
  </tr>
  <tr>
    <td>Generative Language Model</td>
    <td>Creative strategy adaptation</td>
    <td>Model API credentials</td>
  </tr>
  <tr>
    <td>Video Generation Model</td>
    <td>AI video creative generation</td>
    <td>Model API credentials</td>
  </tr>
  <tr>
    <td>Collaboration Platform</td>
    <td>Team notifications</td>
    <td>Bot or webhook token</td>
  </tr>
  <tr>
    <td>Datastore</td>
    <td>Brand data and audit logs</td>
    <td>Read/write access</td>
  </tr>
</table>

<hr />

<h2>2. Environment Preparation</h2>

<h3>2.1 Environment Variable Strategy</h3>
<p>
All secrets and credentials must be externalized using environment variables
or secure credential storage. No secrets are embedded in the workflow definition.
</p>

<h3>2.2 Environment Variable Categories</h3>
<ul>
  <li>External API authentication tokens</li>
  <li>Datastore access credentials</li>
  <li>Notification platform credentials</li>
  <li>Optional feature flags</li>
</ul>

<p>
An <code>env.example</code> file is provided to document required variables without
exposing sensitive values.
</p>

<hr />

<h2>3. Workflow Import Procedure</h2>

<h3>3.1 Workflow File Location</h3>
<p>
The workflow definition is located at:
</p>
<ul>
  <li><code>workflows/ai-ad-creative-strategist.json</code></li>
</ul>

<h3>3.2 Import Steps</h3>
<ol>
  <li>Access the workflow automation platform UI</li>
  <li>Navigate to workflow import functionality</li>
  <li>Select the workflow JSON file</li>
  <li>Confirm successful import</li>
</ol>

<p>
After import, the workflow will appear as a single, disabled workflow pending configuration.
</p>

<hr />

<h2>4. Credential Configuration</h2>

<h3>4.1 Credential Binding Overview</h3>
<p>
The imported workflow references credentials by logical name.
Each reference must be bound to a valid credential configuration.
</p>

<h3>4.2 Required Credential Types</h3>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Credential Type</th>
    <th>Used In</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td>HTTP API Credential</td>
    <td>Competitor Ad Ingestion</td>
    <td>Authenticated API access</td>
  </tr>
  <tr>
    <td>AI Model Credential</td>
    <td>Analysis & Adaptation</td>
    <td>Multimodal and language model invocation</td>
  </tr>
  <tr>
    <td>Datastore Credential</td>
    <td>Persistence Nodes</td>
    <td>Read/write brand and audit data</td>
  </tr>
  <tr>
    <td>Notification Credential</td>
    <td>Notification Nodes</td>
    <td>Team messaging</td>
  </tr>
</table>

<h3>4.3 Configuration Steps</h3>
<ol>
  <li>Create credentials in the platform’s credential manager</li>
  <li>Assign credentials to matching nodes</li>
  <li>Validate connectivity using built-in credential tests</li>
</ol>

<hr />

<h2>5. Brand Data Preparation</h2>

<h3>5.1 Brand Context Requirements</h3>
<p>
Brand context data must exist prior to execution. This data informs creative adaptation.
</p>

<ul>
  <li>Brand name and short identifier</li>
  <li>Value propositions and benefits</li>
  <li>Tone of voice guidelines</li>
  <li>Visual identity attributes</li>
  <li>Product-specific messaging constraints</li>
</ul>

<h3>5.2 Data Consistency Rules</h3>
<ul>
  <li>All required fields must be populated</li>
  <li>Text fields must be human-readable and complete</li>
  <li>Color and visual fields must use consistent formats</li>
</ul>

<hr />

<h2>6. Scheduling and Execution Configuration</h2>

<h3>6.1 Schedule Configuration</h3>
<p>
The workflow is designed to execute on a daily schedule.
</p>

<ul>
  <li>Execution frequency: once per day</li>
  <li>Trigger time: configurable based on operational needs</li>
  <li>Timezone: aligned with business operations</li>
</ul>

<h3>6.2 Execution Scope</h3>
<ul>
  <li>Each run is independent</li>
  <li>Failures are isolated to individual ad iterations</li>
  <li>Partial successes do not block future executions</li>
</ul>

<hr />

<h2>7. Validation and Testing</h2>

<h3>7.1 Pre-Production Validation</h3>
<ol>
  <li>Run workflow manually with a single competitor brand</li>
  <li>Verify ad ingestion results</li>
  <li>Confirm qualification filtering behavior</li>
  <li>Validate AI analysis outputs</li>
  <li>Confirm brand adaptation accuracy</li>
</ol>

<h3>7.2 Output Verification</h3>
<ul>
  <li>Check persisted records in datastore</li>
  <li>Review generated prompts for brand alignment</li>
  <li>Confirm notification delivery</li>
</ul>

<hr />

<h2>8. Operational Safeguards</h2>

<h3>8.1 Human-in-the-Loop Controls</h3>
<ul>
  <li>No automatic ad publishing</li>
  <li>All generated creatives require human review</li>
  <li>Notifications explicitly indicate review status</li>
</ul>

<h3>8.2 Rate and Cost Control</h3>
<ul>
  <li>Batch processing limits external API usage</li>
  <li>Qualification filtering reduces unnecessary AI calls</li>
  <li>Deterministic execution prevents runaway loops</li>
</ul>

<hr />

<h2>9. Security Considerations</h2>

<ul>
  <li>No secrets committed to version control</li>
  <li>All credentials stored securely</li>
  <li>Least-privilege access enforced for external services</li>
  <li>Execution logs retained for auditability</li>
</ul>

<hr />

<h2>10. Maintenance and Updates</h2>

<h3>10.1 Workflow Updates</h3>
<ul>
  <li>Disable workflow before modifying</li>
  <li>Export and version updated workflow JSON</li>
  <li>Re-import and rebind credentials if required</li>
</ul>

<h3>10.2 Brand and Strategy Updates</h3>
<ul>
  <li>Brand data updates do not require workflow changes</li>
  <li>New competitor brands can be added incrementally</li>
</ul>

<hr />

<h2>11. Troubleshooting Guidelines</h2>

<table border="1" cellpadding="6" cellspacing="0">
  <tr>
    <th>Issue</th>
    <th>Likely Cause</th>
    <th>Resolution</th>
  </tr>
  <tr>
    <td>No ads ingested</td>
    <td>API credential or query issue</td>
    <td>Validate credentials and parameters</td>
  </tr>
  <tr>
    <td>No qualified ads</td>
    <td>Overly strict runtime filters</td>
    <td>Adjust qualification thresholds</td>
  </tr>
  <tr>
    <td>Off-brand output</td>
    <td>Incomplete brand data</td>
    <td>Review brand context fields</td>
  </tr>
</table>

<hr />

<h2>12. Conclusion</h2>

<p>
Following this setup guide ensures a secure, deterministic, and production-ready
deployment of the AI Ad Creative Strategist workflow. Proper configuration enables
scalable, repeatable generation of high-quality advertising creatives while maintaining
full human oversight and auditability.
</p>

</body>
</html>
