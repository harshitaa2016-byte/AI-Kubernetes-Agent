AI-Kubernetes-Agent

Build an AI-powered Kubernetes troubleshooting platform that can:
-Investigate Kubernetes failures
-Analyze logs, events, and cluster state
-Identify root causes
-Suggest fixes
-Store investigation history
-Be deployed publicly as a real application




┌────────────────────────────────────────────────────────────┐
│                    Kubernetes Cluster                      │
│                                                            │
│  Pods | Deployments | Services | Events | Logs             │
│                                                            │
│  This is where failures happen and evidence exists.        │
└────────────────────────────────────────────────────────────┘
                          │
                          │ Kubernetes API / kubectl
                          ▼
┌────────────────────────────────────────────────────────────┐
│                  Investigation Layer                       │
│                                                            │
│ Responsibility:                                            │
│ • Connect to Kubernetes cluster                           │
│ • Collect troubleshooting signals                         │
│ • Gather debugging evidence                               │
│                                                            │
│ Components:                                                │
│                                                            │
│ 1. Pod Inspector                                           │
│    • Get pod health                                        │
│    • Detect CrashLoopBackOff                               │
│    • Detect Pending/Error states                           │
│                                                            │
│ 2. Logs Collector                                          │
│    • Read pod logs                                         │
│    • Capture container errors                              │
│                                                            │
│ 3. Events Analyzer                                         │
│    • Read Kubernetes events                                │
│    • Detect scheduling/image failures                      │
│                                                            │
│ 4. Deployment Inspector                                    │
│    • Inspect deployment status                             │
│    • Verify rollout health                                 │
│                                                            │
│ 5. Network Inspector                                       │
│    • Check services                                        │
│    • Validate selectors                                    │
│    • Investigate DNS/networking issues                     │
└────────────────────────────────────────────────────────────┘
                          │
                          │ Structured Investigation Data
                          ▼
┌────────────────────────────────────────────────────────────┐
│                  AI Kubernetes Agent                       │
│                                                            │
│ Responsibility:                                            │
│ • Understand Kubernetes failures                           │
│ • Correlate logs, events, and deployment state             │
│ • Identify root causes                                     │
│ • Recommend fixes                                          │
│                                                            │
│ Components:                                                │
│                                                            │
│ 1. Prompt Builder                                          │
│    • Convert investigation data into an LLM prompt         │
│                                                            │
│ 2. LLM Reasoning Layer                                     │
│    • Uses OpenRouter API key from InsForge                 │
│    • Supports models such as:                              │
│      - Claude                                              │
│      - GPT                                                 │
│      - DeepSeek                                            │
│                                                            │
│ 3. Root Cause Analyzer                                     │
│    • Detect primary issue                                  │
│    • Correlate multiple signals                            │
│                                                            │
│ 4. Fix Recommendation Engine                               │
│    • Suggest kubectl commands                              │
│    • Recommend YAML updates                                │
│                                                            │
│ 5. Confidence Scoring                                      │
│    • Provide confidence percentage                         │
└────────────────────────────────────────────────────────────┘
                          │
                          │ Investigation Result
                          ▼
┌────────────────────────────────────────────────────────────┐
│                    InsForge Backend                        │
│                                                            │
│ Responsibility:                                            │
│ • Authentication                                           │
│ • Backend APIs                                             │
│ • Investigation history                                    │
│ • Real-time investigation updates                          │
│                                                            │
│ Components:                                                │
│                                                            │
│ 1. Authentication                                          │
│    • User login                                            │
│                                                            │
│ 2. API Layer                                               │
│    • Trigger investigations                                │
│    • Return AI analysis                                    │
│                                                            │
│ 3. Investigation History                                   │
│    • Store previous incidents                              │
│    • Save root cause reports                               │
│                                                            │
│ 4. Real-time Updates                                       │
│    • Live investigation progress                           │
│                                                            │
│ Example Progress:                                          │
│ ✓ Checking Pods                                            │
│ ✓ Reading Logs                                             │
│ ✓ Analyzing Events                                         │
│ ✓ Finding Root Cause                                       │
└────────────────────────────────────────────────────────────┘
                          │
                          │ API Response
                          ▼
┌────────────────────────────────────────────────────────────┐
│                 Frontend Dashboard                         │
│                                                            │
│ Responsibility:                                            │
│ • Trigger investigations                                   │
│ • Show real-time progress                                  │
│ • Display root cause                                       │
│ • Show suggested fixes                                     │
│ • Display investigation history                            │
│                                                            │
│ Example UI:                                                │
│                                                            │
│ Incident: Payment Service Failure                          │
│                                                            │
│ Status: Investigating...                                   │
│                                                            │
│ ✓ Pods Checked                                             │
│ ✓ Events Analyzed                                          │
│ ✓ Logs Processed                                           │
│                                                            │
│ Root Cause: ImagePullBackOff                               │
│                                                            │
│ Suggested Fix:                                             │
│ Update the invalid image tag                               │
└────────────────────────────────────────────────────────────┘
                          │
                          ▼
┌────────────────────────────────────────────────────────────┐
│                 InsForge Deployment                        │
│                                                            │
│ Responsibility:                                            │
│ • Deploy frontend                                          │
│ • Deploy backend                                           │
│ • Generate public URL                                      │
│                                                            │
│ Output:                                                    │
│ https://ai-k8s-agent.public-url.app                        │
│                                                            │
│ Enables public access to the troubleshooting platform.     │
└────────────────────────────────────────────────────────────┘

Example Failure Flow
Issue
Payment service unavailable
Agent Investigation
✅ Pod status checked
✅ Logs collected
✅ Events analyzed
Detected Problem
CrashLoopBackOff
Root Cause
DATABASE_URL environment variable is missing.
Confidence
94%
Suggested Fix
Update deployment.yaml and add the required Secret reference.
Prevention
Add startup validation checks to ensure all required environment variables are present before application startup.
Supported Kubernetes Problems
CrashLoopBackOff
ImagePullBackOff
OOMKilled
Pending Pods
Resource Exhaustion
Deployment Rollout Failures
Service Selector Mismatch
DNS Resolution Problems
Readiness Probe Failures
Liveness Probe Failures
Networking Issues

