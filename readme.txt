Reference:
https://www.baeldung.com/kubernetes-helm


Creating a Chart:
- "helm create hello-world": this created a folder hello-world

Creating Template:
- In the folder hello-world/templates/, then edit deployment.yaml and service.yaml.

Providing Values:
- We typically pass values through Built-in Objects in Helm.
- There are many such objects available in Helm, like Release, Values, Chart, and Files.
- We can use the file values.yaml in our chart to pass values to the template rendering engine 
  through the Built-in Object Values.
- These values will be accessed within templates using dots separating namespaces.
- Edit hello-world/values.yaml

Lint and render package locally:
- "helm lint ./hello-world": runs a battery of tests to ensure that the chart is well-formed.
- "helm template ./hello-world": render template locally for quick feedback.

Start the kubernetes cluster and start dashboard to watch the status:
- "minikube start"
- "minikube dashboard"

Install Helm chart:
- "helm install hello-world ./hello-world": install the chart into the Kubernetes cluster.
- "helm ls --all": query the named releases, list which charts are installed as what release.

Optional: can also upgrade or delete chart:
- "helm upgrade hello-world ./hello-world": chart was modified, upgrade a release to a specified 
  or current version of the chart or configuration.
- "helm rollback hello-world 1": rollback a release to the previous version.
- "helm delete hello-world": delete a release from Kubernetes.

Distributing Charts:
- Helm acts as a package manager for the Kubernetes application and makes installing, querying, 
  upgrading, and deleting releases pretty seamless.
- In addition to this, Helm comes with commands as part of its CLI to package, publish, and fetch 
  Kubernetes applications as charts.
- "helm package ./hello-world": create versioned archive files of the chart, package the charts 
  you have created to be able to distribute them.
- We can create a git repository and use that to function as our chart repository. The only 
  requirement is that it should have an index.yaml file.
- "helm repo index <folder>/ --url https://<username>.github.io/<repo-name>": create index.yaml 
  for the chart repo. 
  - folder: folder path, e.g., "." (current folder) or any other folder name.
  - username: e.g., "liupeng69"
  - repo-name: e.g., "helm-chart-hello-world".
- 
