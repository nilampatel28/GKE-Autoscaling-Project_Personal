# GKE-Autoscaling-Project_Personal
Applied GKE Autoscaling Strategies (HPA, VPA, Cluster Autoscaler, NAP) to optimize performance and cost in a production-grade environment.


Project Title:

GKE Autoscaling Optimization Project – Implementing HPA, VPA, and Cluster Autoscaler with Node Auto Provisioning

Q1. What was the project objective?

Ans:
To design and implement a self-optimizing Kubernetes cluster on Google Kubernetes Engine (GKE) that can automatically adjust resources and scale workloads efficiently.
The main goal was to combine multiple autoscaling strategies — Horizontal Pod Autoscaler (HPA), Vertical Pod Autoscaler (VPA), Cluster Autoscaler, and Node Auto Provisioning (NAP) — to achieve performance consistency and cost optimization.

Q2. What tools and technologies were used?

Ans:

Google Kubernetes Engine (GKE) – Cluster orchestration.

Kubernetes Autoscaling APIs – HPA, VPA, and Cluster Autoscaler.

Node Auto Provisioning (NAP) – Automated node pool creation.

Google Cloud Monitoring & Metrics Server – Metrics collection.

kubectl, YAML manifests, and Cloud Shell – Deployment and automation.

Linux shell scripting – Test load generation and monitoring.

Q3. How was the project implemented?

Ans:
The implementation followed a systematic setup and validation process.


Step 1 – Cluster Setup

Created a GKE cluster with autoscaling enabled and monitoring agents installed.

Verified metrics collection via metrics-server and Cloud Monitoring.

⚙️ Step 2 – Application Deployment

Deployed a sample video processing application as a Kubernetes Deployment with defined CPU requests/limits.

Configured the Cluster Autoscaler to scale nodes between 2 and 5 automatically.

📈 Step 3 – Applied Horizontal Pod Autoscaler (HPA)

Configured an HPA using CPU utilization as the metric trigger.

Command used:

kubectl autoscale deployment video-processor --cpu-percent=80 --min=1 --max=7

⚙️ Step 4 – Enabled Vertical Pod Autoscaler (VPA)

Created a VPA manifest to automatically recommend and apply optimal CPU and memory for the pods.

updatePolicy:
  updateMode: "Auto"

🌐 Step 5 – Enabled Node Auto Provisioning (NAP)

Enabled NAP in GKE to allow on-demand creation of new node pools for varying workload patterns.

Tested it by generating high load and observing new nodes being created automatically.

💾 Step 6 – Implemented Overprovisioning

Deployed pause pods to pre-allocate minimal resources ensuring zero cold start delay.

📊 Step 7 – Validation

Generated CPU load using stress tools.

Observed pod scaling and node creation in Cloud Monitoring → Metrics Explorer.

Verified smooth scale-down after load reduction.

Q4. What were the project outcomes?

Ans:
✅ The GKE cluster successfully scaled pods and nodes based on demand.
✅ CPU and memory usage remained within defined SLO thresholds.
✅ Idle nodes were automatically removed, optimizing costs by 20–25% (simulated).
✅ The system achieved zero manual intervention scaling during workload peaks.
✅ Demonstrated full lifecycle: HPA → VPA → Cluster Autoscaler → NAP.

Q5. What skills were demonstrated?

Ans:

GKE cluster configuration and management

Kubernetes autoscaling design

Resource optimization and observability

YAML automation for Kubernetes

Cloud Monitoring metric analysis

DevOps mindset for cost-efficient scaling

Q6. What was the key learning or takeaway?

Ans:

Smart autoscaling isn’t just about expanding capacity — it’s about building clusters that think, adapt, and optimize themselves based on real-time workload demands.

Final Outcome Summary:
Component	Purpose	Validation Result
HPA	Pod-level scaling	Scaled 1→7 replicas
VPA	Resource tuning	Adjusted CPU/memory automatically
Cluster Autoscaler	Node scaling	Nodes increased from 2→3
NAP	Dynamic pool creation	Created optimized node pool
Overprovisioning	Zero cold start delay	Smooth load handling
Q7. How can this project be extended?

Ans:
In a real enterprise setup, this can be extended by:

Integrating Terraform and Helm for IaC-based deployment.

Adding cost dashboards via BigQuery and Prometheus metrics.

Implementing safe HPA+VPA combination using recommendation mode.
