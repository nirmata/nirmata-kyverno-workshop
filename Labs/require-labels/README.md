# Check Lables Policy

This hands-on lab demonstrates how to create and apply a Kyverno policy that prevents containers with specific label from being deployed in your cluster.

## What You'll Learn

- How to write a policy that blocks privileged container deployments
- How to validate policies using Kyverno CLI
- How to perform end-to-end testing using Chainsaw tests

## Background
Labels in Kubernetes provide a way to attach metadata to objects, enabling better organization, filtering, and management of resources. 
This policy enforces the presence of a chosen label on Pod resources. By requiring standardized labels, organizations can:

  * Improve resource organization and discoverability
  * Enable consistent filtering and querying of resources
  * Support better cost allocation and resource tracking
  * Enhance automation and tooling integration
  * Maintain compliance with organizational standards

## Try It Out

1. To apply the policy on a cluster:
```bash
kubectl apply -f require-labels.yaml
```

2. Check that the policy staus "READY" is set to "True", and the "MESSAGE" is set to "Ready":
```bash
kubectl get cpol
```

## Manual Test

Remove the policies and test resources:
```bash
kubectl delete -f .
```

## Notes

- For production use, consider using KMS or cloud provider key management services
- Implement proper key rotation and management procedures
- Consider using policy exceptions for development/testing environments 
