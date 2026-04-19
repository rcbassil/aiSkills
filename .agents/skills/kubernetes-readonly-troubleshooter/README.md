# Kubernetes Read-Only Troubleshooter

`kubernetes-readonly-troubleshooter` is an AI agent skill designed for safely diagnosing and investigating issues within Kubernetes clusters and microservice architectures. It acts as a DevSecOps assistant with **strict read-only constraints**, ensuring that it will never modify, create, update, or delete any resources in your cluster.

## Features

* **Zero-Touch Analysis:** Diagnoses problems safely without executing any state-altering commands (no `kubectl apply`, `delete`, `edit`, `scale`, `patch`, `helm install/upgrade`, or even `kubectl debug`).
* **Deep Log Inspection:** Analyzes container outputs, including failing `initContainers` and previously crashed instances.
* **Network & Routing Tracing:** Investigates Ingress, API Gateways (like Kong), Services, and endpoints to identify connectivity drops or missing configurations.
* **RBAC & Security Constraints:** Examines RoleBindings, network policies, and security contexts that might be denying access.
* **GitOps Troubleshooting:** Checks application synchronization states (such as FluxCD reconciliation loops).

## When to use this skill

Invoke this skill whenever you need to:
* Find the root cause of a `CrashLoopBackOff`, `ImagePullBackOff`, or `Pending` pod.
* Trace why traffic is not reaching your microservice.
* Validate configuration mappings (ConfigMaps, Secrets, PVCs) securely.
* Ensure absolute safety by preventing the AI agent from accidentally modifying cluster resources during the troubleshooting process.

## How to use

Simply ask the agent to investigate a specific namespace, pod, or microservice using read-only techniques:

> "My `payment-service` pod in the `production` namespace keeps crashing. Please use your read-only troubleshooter to find the root cause."

> "Can you execute a read-only investigation to see why the API gateway isn't routing traffic to the `user-auth` endpoints?"

The agent will use `kubectl get`, `kubectl describe`, and `kubectl logs` to gather evidence, identify configuration mismatches, and provide a text-based, actionable recommendation for you to apply manually.
