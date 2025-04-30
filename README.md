# PaC-workshop with Kyverno

## Pre-Requisites
To get the most out of this workshop, you'll need access to a Kubernetes cluster.  You can use a local single-node cluster environment such as:

* **kind:** [https://kind.sigs.k8s.io/docs/user/quick-start/](https://kind.sigs.k8s.io/docs/user/quick-start/)
* **minikube:** [https://minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)
* **k3d:** [https://k3d.io/v5.4.6/usage/](https://k3d.io/v5.4.6/usage/)

## Kyverno Documentation & Resources

* **Kyverno Official Documentation:** [https://kyverno.io/docs/](https://kyverno.io/docs/) -  The official source for all things Kyverno.
* **Kyverno Policy Library:**
    * **Kyverno website:** [https://kyverno.io/policies/](https://kyverno.io/policies/) -  A collection of ready-to-use Kyverno policies.
    * **Github repo:** [https://github.com/kyverno/policies/](https://github.com/kyverno/policies/) - The source code for the policy library, allowing you to contribute or policies.

## Tools for Testing

* **Kyverno CLI:** [https://kyverno.io/docs/kyverno-cli/install/](https://kyverno.io/docs/kyverno-cli/install/) - A tool for performing unit tests on Kyverno policies.
* **Install Chainsaw:** [ihttps://kyverno.github.io/chainsaw/latest/quick-start/install/](https://kyverno.github.io/chainsaw/latest/quick-start/install/) - A framework for E2E testing of policies.

## Workshop Agenda


This workshop is structured to guide you from the fundamentals of Kyverno to more advanced use cases.

**1. Introduction to Kyverno**

* Overview of Policy-as-Code.
* Kyverno's architecture and core concepts.

**2. Writing Validation Policies**

   We'll focus on writing, deploying, and testing validation policies to enforce constraints on Kubernetes resources.

   * **Require Labels:** Ensure that specific labels are applied to resources for organizational and management purposes.
   * **Pod Security Standards:** Implement policies to enforce security best practices for Pods.

**3. Advanced Kyverno Policy Use Cases**

   Explore Kyverno's powerful capabilities beyond basic validation.

   * **Mutating Policy:** Automatically modify resources, such as adding defaults or annotations.
   * **Generating Policy:** Create new Kubernetes resources based on existing ones, automating tasks like creating ConfigMaps or Secrets.
   * **Image Verification Policy:** Implement policies to ensure that only trusted container images are deployed in your cluster, enhancing security.
   * **Resource Optimization:** Explore policies that can help optimize resource utilization.
