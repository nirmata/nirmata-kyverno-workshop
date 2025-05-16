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

## Testing the Policy Manually

1. There's a resource file in `.kyverno-test` folder which can be used to test the deployed policy.
2. From the `require-labels` folder, apply the `resource.yaml` file using the command
   ```
   kubectl apply -f .kyverno-test/resource.yaml
   ```
3. As the policy is deployed in `Audit` mode, the resoueces are allowed to be deployed while logging the violations. Check the policy violations using the command
   ```
   kubectl get polr
   ```
   Note: The policy reports are tagged to the namespace, so any resources that are deployed in non-default namespaces should be verified using the `-n <namespace>` suffix to the above command.

4. Clean up the created resources and policies using the following commands
   ```
   kubectl delete cpol require-labels
   kubectl delete -f .kyverno-test/resouece.yaml
   ```

## Kyverno CLI Test
Kyverno CLI test is a unit test that validates the policy and evaluates against a pre-defined k8s resource(s) before applying them to a live cluster.
 * Step 1: Navigate to the `.kyverno-test` folder
 * Step 2: Update the `resource.yaml` file with good-pod and bad-pod examples that pass and fail the policy criteria
 * Step 3: Update the `kyverno-test.yaml` file to manually specify which resources fail the policy and which ones pass
 * Step 4: Run the kyverno CLI test using the command:
 ```bash
 kyverno test .
 ```

## Chainsaw Test
Chainsaw test is an E2E testing tool that's designed to simulate real-world scenarios within a live cluster or a simulated one like KinD. It allows to define sequences of actions (apply, update, delete etc.), and assert the resulting state of the cluster.
 * Step 1: Navigate to the `.chainsaw-test` folder
 * Step 2: Update the `good-resource.yaml` file with the resources that pass the policy criteria and `bad-resource.yaml` file with bad-pod examples that fail the policy criteria
 * Step 3: Update the `policy-assert.yaml` file with the expected status of policy after applying
 * Step 4: `chainsaw-test.yaml` file specifies which resources pass when applied and are expected to fail (good-resources and bad-resources)
 * Step 5: Run the chainsaw test using the command:
 ```bash
 chainsaw test 
 ```

Remove the policies and test resources:
```bash
kubectl delete -f .
```
