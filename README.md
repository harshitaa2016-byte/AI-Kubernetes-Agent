# High Level Architecture

```text

Build an AI-powered Kubernetes troubleshooting platform that can: 
-Investigate Kubernetes failures
-Analyze logs, events, and cluster state 
-Identify root causes 
-Suggest fixes 
-Store investigation history 
-Be deployed publicly as a real application 

+----------------------------------------------------------+
|                 Kubernetes Cluster                       |
|----------------------------------------------------------|
| Pods | Deployments | Services | Events | Logs            |
|                                                          |
| Failures occur here and evidence is collected here.      |
+----------------------------------------------------------+

              Kubernetes API / kubectl
                          |
                          v
+----------------------------------------------------------+
|                 Investigation Layer                      |
|----------------------------------------------------------|
| Responsibilities:                                        |
| - Connect to Kubernetes cluster                          |
| - Collect troubleshooting signals                        |
| - Gather debugging evidence                              |
|                                                          |
| Components:                                              |
| 1. Pod Inspector                                         |
| 2. Logs Collector                                        |
| 3. Events Analyzer                                       |
| 4. Deployment Inspector                                  |
| 5. Network Inspector                                     |
+----------------------------------------------------------+

                Structured Investigation Data
                          | 
                          v
+----------------------------------------------------------+
|                  AI Kubernetes Agent                     |
|----------------------------------------------------------|
|  Responsibility:                                            │
│ - Understand Kubernetes failures                           │
│ - Correlate logs + events + deployment state               │
│ - Identify root cause                                      │
│ - Recommend fixes                                          │
│                                                            │
│ Components:                                                │
│                                                            │
│  1. Prompt Builder                                         │
│     - Convert investigation data into LLM prompt           │
│                                                            │
│  2. LLM Reasoning Layer                                    │
│     - Uses OpenRouter API Key from InsForge                │
│     - Supports models like:                                │
│       - Claude                                              │
│       - GPT                                                 │
│       - DeepSeek                                            │
│                                                            │
│  3. Root Cause Analyzer                                    │
│     - Detect primary issue                                 │
│     - Correlate signals                                    │
│                                                            │
│  4. Fix Recommendation Engine                              │
│     - Suggest kubectl fixes                                │
│     - Recommend YAML updates                               │
│                                                            │
│  5. Confidence Scoring                                     │
│     - Confidence % for diagnosis |
+----------------------------------------------------------+
                 Investigation Result
                          | 
                          v
+----------------------------------------------------------+
|                  InsForge Backend                        |
|----------------------------------------------------------|
| Authentication                                           |
| Backend APIs                                             |
| Investigation History                                    |
| Realtime Updates                                         |
+----------------------------------------------------------+
                    API Response
                          |
                          v
+----------------------------------------------------------+
|                 Frontend Dashboard                       |
|----------------------------------------------------------|
| Trigger Investigation                                    |
| Show Progress                                            |
| Display Root Cause                                       |
| Suggested Fixes                                          |
| Investigation History                                    |
+----------------------------------------------------------+
                          |
                          v
+----------------------------------------------------------+
|                Public Deployment                         |
|----------------------------------------------------------|
| https://ai-k8s-agent.public-url.app                      |
+----------------------------------------------------------+
```

Supported Kubernetes Problems:

CrashLoopBackOff
ImagePullBackOff
OOMKilled
Pending Pods
Resource Exhaustion
Deployment Rollout Failures
Service Selector Mismatch
DNS Resolution Problems
Readiness/Liveness Probe Failures
Networking Issues
