# kubernetes_deployment_manif

**Tweet URL:** [/markontechcom/status/1888703569395654704](/markontechcom/status/1888703569395654704)

**Tweet Text:** ** Kubernetes deployment manifest file structure explained **

In the Kubernetes deployment YAML we define how an application should be deployed and managed within a Kubernetes cluster. 

Below is a breakdown of the YAML structure with explanations.

** Explanation of the key sections **

- apiVersion & kind: Defines that this is a deployment resource and uses apps/v1 Kubernetes API.
- metadata: Contains details like the name and labels for app organization.
- spec.replicas: Defines the desired number of running instances (pods).
- spec.selector.matchLabels: Ensures the deployment controls only pods with matching labels.
- spec.template:
   - Defines the pod template (metadata and spec).
   - The containers section defines container details such as the image, ports, and resources.
   - Environment variables, volume mounts, and resource limits can also be set.
- spec.strategy: Controls the deployment update strategy (RollingUpdate or Recreate).
- volumes: Allows defining persistent storage like ConfigMaps, Secrets, or Persistent Volumes.

** Optional additions **

    - Liveness & Readiness Probes (for health checks)
    - Affinity & Node Selectors (for scheduling)
    - Init Containers (for pre-processing tasks)

**Image 1 Description:** The image shows a code snippet in a text editor, likely Visual Studio Code, with a dark theme. The code is written in Markdown syntax and appears to be a deployment manifest for Kubernetes.

Here are the details of the code:

* **Header**: The header at the top of the image reads "Deployment manifest(markontech.com)".
	+ The text is centered and displayed in white font on a dark gray background.
* **Code**: Below the header, there is a large block of code written in Markdown syntax.
	+ The code is formatted with indentation and line breaks for readability.
	+ It appears to be a deployment manifest for Kubernetes, defining various resources such as pods, services, and deployments.
* **Syntax Highlighting**: The code has been highlighted with different colors to indicate the type of syntax being used.
	+ Keywords like "apiVersion", "kind", and "metadata" are highlighted in blue.
	+ Other elements like lists and tables are highlighted in green or yellow.
* **Navigation Bar**: At the top of the image, there is a navigation bar with buttons for navigating through the code file.
	+ The buttons are labeled with icons representing different actions, such as "New File", "Open File", and "Save".
	+ The navigation bar is displayed in white font on a dark gray background.

Overall, the image shows a deployment manifest for Kubernetes written in Markdown syntax and formatted with indentation and line breaks for readability. The code has been highlighted with different colors to indicate the type of syntax being used, making it easier to read and understand.
![Image 1](./image_1.jpg)
