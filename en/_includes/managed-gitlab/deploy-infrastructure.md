### Prepare the infrastructure {#deploy-infrastructure}

{% list tabs %}

- Manually

   1. If you do not have a [network](../../vpc/concepts/network.md#network), [create one](../../vpc/operations/network-create.md).
   1. If you do not have any [subnets](../../vpc/concepts/network.md#subnet), [create them](../../vpc/operations/subnet-create.md) in the [availability zones](../../overview/concepts/geo-scope.md) where your [{{ managed-k8s-full-name }} cluster](../../managed-kubernetes/concepts/index.md#kubernetes-cluster) and [node group](../../managed-kubernetes/concepts/index.md#node-group) will be created.
   1. [Create service accounts](../../iam/operations/sa/create.md):
      * [Service account](../../iam/concepts/users/service-accounts.md) for the resources with the [{{ roles-editor }}](../../resource-manager/security/index.md#roles-list) [role](../../iam/concepts/access-control/roles.md) for the [folder](../../resource-manager/concepts/resources-hierarchy.md#folder) where the {{ managed-k8s-name }} cluster is being created. The resources the {{ managed-k8s-name }} cluster needs will be created on behalf of this account.
      * Service account for nodes with the [{{ roles-cr-puller }}](../../container-registry/security/index.md#service-roles) role for the folder with the [Docker image](../../container-registry/concepts/docker-image.md) [registry](../../container-registry/concepts/registry.md). {{ managed-k8s-name }} nodes will pull the required Docker images from the registry on behalf of this account.

      {% note tip %}

      You can use the same service account for both operations.

      {% endnote %}

   1. [Create a {{ managed-k8s-name }} cluster](../../managed-kubernetes/operations/kubernetes-cluster/kubernetes-cluster-create.md#kubernetes-cluster-create) and a [node group](../../managed-kubernetes/operations/node-group/node-group-create.md). When creating a {{ managed-k8s-name }} cluster, specify the previously created service accounts for the resources and nodes.
   1. [Configure security groups](../../managed-kubernetes/operations/connect/security-groups.md) for the {{ managed-k8s-name }} cluster to run.
   1. [Configure the default security group](../../managed-gitlab/operations/connect.md) required for the [{{ mgl-name }} instance](../../managed-gitlab/concepts/index.md#instance) to run.
   1. [Create a registry in {{ container-registry-full-name }}](../../container-registry/operations/registry/registry-create.md).

- Using {{ TF }}

   1. If you do not have {{ TF }} yet, [install and configure it](../../tutorials/infrastructure-management/terraform-quickstart.md#install-terraform).
   1. Download the [file with provider settings](https://github.com/yandex-cloud/examples/tree/master/tutorials/terraform/provider.tf). Place it in a separate working directory and [specify the parameter values](../../tutorials/infrastructure-management/terraform-quickstart.md#configure-provider).
   1. Download the [k8s-gl.tf](https://github.com/yandex-cloud/examples/blob/master/tutorials/terraform/managed-kubernetes/k8s-gl.tf) configuration file to the same working directory.

      This file describes:
      * [Network](../../vpc/concepts/network.md#network).
      * [Subnet](../../vpc/concepts/network.md#subnet).
      * [Default security group](../../vpc/concepts/security-groups.md) and rules needed to run the [{{ mgl-name }} instance](../../managed-gitlab/concepts/index.md#instance).
      * [Security group](../../vpc/concepts/security-groups.md) and rules required for running the [{{ managed-k8s-full-name }} cluster](../../managed-kubernetes/concepts/index.md#kubernetes-cluster).
      * {{ managed-k8s-name }} cluster.
      * [Service account](../../iam/concepts/users/service-accounts.md) required to use the cluster and [{{ managed-k8s-name }} node group](../../managed-kubernetes/concepts/index.md#node-group).
      * {{ container-registry-full-name }} [registry](../../container-registry/concepts/registry.md).
   1. In `k8s-gl.tf`, specify:
      * [Folder ID](../../resource-manager/operations/folder/get-id.md).
      * [{{ k8s }} version](../../managed-kubernetes/concepts/release-channels-and-updates.md) for the {{ managed-k8s-name }} cluster and node groups.
      * {{ managed-k8s-name }} cluster CIDR.
      * Name of the {{ managed-k8s-name }} cluster service account.
      * Name of the {{ container-registry-name }} registry.
   1. Run the `terraform init` command in the directory with the configuration file. This command initializes the provider specified in the configuration files and enables you to use the provider resources and data sources.
   1. Make sure the {{ TF }} configuration files are correct using this command:

      ```bash
      terraform validate
      ```

      If there are any errors in the configuration files, {{ TF }} will point them out.
   1. Create the required infrastructure:

      {% include [terraform-apply](../../_includes/mdb/terraform/apply.md) %}

      {% include [explore-resources](../../_includes/mdb/terraform/explore-resources.md) %}

{% endlist %}
