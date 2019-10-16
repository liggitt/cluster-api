# Cluster API v1alpha2 compared to v1alpha3

## In-Tree bootstrap provider

- Cluster API now ships with the Kubeadm Bootstrap provider (CABPK).
- Update import paths from `sigs.k8s.io/cluster-api-bootstrap-provider-kubeadm` to `sigs.k8s.io/cluster-api/bootstrap/kubeadm`.

## Machine `spec.metadata` field has been removed

- The field has been unused for quite some time and didn't have any function.
- If you have been using this field to setup MachineSet or MachineDeployment, switch to MachineTemplate's metadata instead.

## Set `spec.clusterName` on Machine, MachineSet, MachineDeployments.

- The field is now required on all Cluster dependant objects.
- The `cluster.x-k8s.io/cluster-name` label is created automatically by each respective controller.

## Context is now required for `external.CloneTemplate` function.

- Pass a context as first argument to calls to `external.CloneTemplate`.

## Cluster and Machine `Status.Phase` field values now start with an uppercase letter.

- To be consistent with Pod phases in k/k.
- More details in https://github.com/kubernetes-sigs/cluster-api/pull/1532/files.