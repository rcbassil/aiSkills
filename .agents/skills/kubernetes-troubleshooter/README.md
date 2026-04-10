# Kubernetes Troubleshooter Skill

This skill turns your AI assistant into a powerful **DevSecOps Kubernetes specialist**. It is designed to diagnose, troubleshoot, and fix issues in Kubernetes clusters, with extended support for microservice architectures, GitOps workflows (FluxCD), and API Gateways (Kong).

## Capabilities

The skill automatically directs the assistant to systematically investigate:
- **Core Workloads & Resources**: Pods, Deployments, PVCs, resource limitations, and scheduling errors.
- **Application Logs**: Container logs, initContainers, and previous crash logs.
- **Microservices & Networking**: Tracing routes from Ingress and Kong Gateway definitions down to Services and healthy pod endpoints.
- **GitOps Deployments**: Diagnosing FluxCD resource reconciliation issues (Kustomizations, HelmReleases).
- **Security & Authorization**: Highlighting RBAC or Pod Security constraints preventing workloads from operating correctly.

## How to Use

You don't need to learn new commands. Simply ask the assistant to investigate your cluster, and it will read the rules of this skill to perform a methodical deep-dive using standard utilities like `kubectl`, `flux`, or Kong commands (assuming the assistant has local CLI access).

### Example Prompts

Here are a few ways you can prompt the assistant to trigger troubleshooting:

**1. Debugging a Crash Loop or Failing Pod**
> "Can you figure out why the `auth-service` in the `production` namespace is in a CrashLoopBackOff state?"

**2. Troubleshooting GitOps / FluxCD Sync Issues**
> "FluxCD seems to be failing to apply the latest manifest changes for the `backend-app`. Can you investigate the Kustomization errors and find the root cause?"

**3. API Gateway / Network Routing Issues**
> "Our Kong Ingress is returning a 502 Bad Gateway when trying to reach the `payment-service`. Can you trace the configuration from the Kong ingress rule down to the pod endpoints to see what's broken?"

**4. General Health Checks**
> "Run a general check on the `staging` namespace and let me know if there are any resource constraints, failing deployments, or recent warning events."

## Requirements

For the assistant to fully leverage this skill, ensure that the environment running the assistant has:
1. `kubectl` installed and configured with a valid kubeconfig pointing to your target cluster.
2. `flux` CLI installed (if debugging FluxCD).
3. Appropriate cluster permissions to read resources, events, and logs.
