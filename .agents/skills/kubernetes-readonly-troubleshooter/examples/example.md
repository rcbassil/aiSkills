# Example: Diagnosing a Crashing Microservice

This example demonstrates how to use the `kubernetes-readonly-troubleshooter` skill to safely find the root cause of an application crash without modifying the cluster.

## User Request

> "My `inventory-api` in the `backend` namespace is in a `CrashLoopBackOff` state. Please investigate securely and tell me what to fix."

## Agent Execution (Read-Only Process)

1. **State Gathering:**
   The agent checks the status of the pods in the namespace:
   ```bash
   kubectl get pods -n backend -l app=inventory-api
   ```
   *Observation: One pod is in `CrashLoopBackOff` with 5 restarts.*

2. **Deep Inspection:**
   The agent describes the pod to see events and configurations:
   ```bash
   kubectl describe pod inventory-api-6b7f8c9b-abcde -n backend
   ```
   *Observation: The "Events" section shows the container starting and then failing. The configuration specifies a secret mount called `db-credentials`.*

3. **Log Analysis:**
   The agent retrieves the logs for the crashed container:
   ```bash
   kubectl logs inventory-api-6b7f8c9b-abcde --previous -n backend
   ```
   *Observation: The logs reveal the following error: `FATAL: password authentication failed for user "inventory_admin". Cause: connection details invalid.`*

4. **Resource Verification:**
   The agent inspects the related secret to verify its structure (without exposing sensitive values if it can be avoided, or just describing the keys):
   ```bash
   kubectl describe secret db-credentials -n backend
   ```
   *Observation: The secret has keys `username`, `host`, but is missing the required `password` key.*

## Agent Response & Recommendation

The agent responds based strictly on its read-only findings:

> **Root Cause Identified:**
> The `inventory-api` pod is crashing because it cannot authenticate with the database. Specifically, the Kubernetes Secret `db-credentials` mounted by this pod is missing the required `password` key, which causes the application to fail during initialization.
> 
> **Recommended Fix:**
> You need to update your Secret manifest to include the missing database password. 
> 
> Update your original `secret.yaml` payload like so:
> ```yaml
> apiVersion: v1
> kind: Secret
> metadata:
>   name: db-credentials
>   namespace: backend
> type: Opaque
> data:
>   username: <base64-encoded-username>
>   host: <base64-encoded-host>
>   password: <base64-encoded-password> # <-- Add this line
> ```
> 
> Once updated, apply the change manually:
> `kubectl apply -f secret.yaml`
> 
> *Note: I have not executed any commands to alter your cluster or restart the pod to maintain strict read-only security.*
