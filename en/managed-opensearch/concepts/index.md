# Relationships between resources in {{ mos-name }}

With {{ mos-full-name }}, you can deploy and maintain {{ OS }} server clusters in the {{ yandex-cloud }} infrastructure.

{{ OS }} is a set of search and analytical resources for real-time application monitoring, log analysis, and search across websites. {{ OS }} clusters consist of one or more host groups with various resources that handle a variety of tasks.

When [creating a cluster](../operations/cluster-create.md), specify the following:

- [_Host classes_](instance-types.md): VM templates for deploying the cluster hosts.

- [_Host groups_](host-groups.md): Sets of multiple linked hosts with specific characteristics and [roles](hosts-roles.md):

   - [_DATA_](hosts-roles.md#data).
   - [_MANAGER_](hosts-roles.md#manager).
   - [_DASHBOARDS_](hosts-roles.md#dashboards).

- _Environment_ where the cluster will be deployed:

   - `PRODUCTION`: For stable versions of your apps.
   - `PRESTABLE`: For testing, including the {{ mos-name }} service itself. The Prestable environment is first updated with new features, improvements, and bug fixes. However, not every update ensures backward compatibility.

- `admin` _user password_.

   {% include [mos-superuser](../../_includes/mdb/mos/superuser.md)%}

- {{ OS }} _version_.


An {{ OS }} cluster created in a folder can be accessed by all VMs connected to the same [cloud network](../../vpc/concepts/network.md) as the cluster.


A cluster with a single-host group doesn't guarantee fault tolerance. A cluster with multiple hosts automatically provides fault tolerance for the `MANAGER` role. To ensure data safety in such a cluster, you need to configure index [sharding and replication](scalability-and-resilience.md).

Cluster hosts may reside in different availability zones and subnets. Learn more about the geo scope of {{ yandex-cloud }} in [{#T}](../../overview/concepts/geo-scope.md).

{% include [monitoring-access](../../_includes/mdb/monitoring-access.md) %}
