- [Introduction](#sec-1)
    - [Apps endpoints](#sec-1-0-1)
    - ["Scale" endpoints for Deployment, Statefulset & Replicaset](#sec-1-0-2)


# Introduction<a id="sec-1"></a>

The aim is that all GA API Endpoints should have conformance tests. No new endpoints should be introduced to GA without conformance tests. The current technical debt consist of Endpoints introduced in historical releases without conformance tests. A concerted effort by the community, SIG's and ii have helped to remove all technical debt back to 1.11. 1.10 & 1.11 have 7 endpoints without conformance tests which are currently being addressed. The next block of endpoints that need to be addressed is release 1.9 where there are 33 endpoints without conformance test. All these endpoints belong to the Apps API group.

The aim of this document is to collect information on tested points and the test the brought them to conformance. Collect information on untested endpoints and the relationship between then and also list documentation on those endpoints that will aid in writing conformance tests.

### Apps endpoints<a id="sec-1-0-1"></a>

According to APISNoop there is a total of 63 GA Apps endpoints at the start of 1.21. 33 of these endpoints, all released to GA in 1.9 do not have conformance tests. The endpoints can be broken down in to 5 "families" which are:

-   Deployment
-   Statefulset
-   Replicaset
-   Daemonset
-   ControllerRevision

We will now list the endpoints by families and groups with documentation reference.

1.  Deployment

    Untested Endpoints:
    
    -   patchAppsV1NamespacedDeploymentScale
    -   readAppsV1NamespacedDeploymentScale
    -   replaceAppsV1NamespacedDeploymentScale See below for "Scale" endpoints.
    
    -   replaceAppsV1NamespacedDeploymentStatus An attempt at conformance testing was made in this [test](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/deployment.go#L337-L358)

2.  Statefulset

    Untested Endpoints:
    
    -   patchAppsV1NamespacedStatefulSet
    -   patchAppsV1NamespacedStatefulSetScale
    
    -   patchAppsV1NamespacedStatefulSetStatus
    -   readAppsV1NamespacedStatefulSetStatus
    -   replaceAppsV1NamespacedStatefulSetStatus
    
    -   listAppsV1StatefulSetForAllNamespaces
    -   deleteAppsV1CollectionNamespacedStatefulSet
    
    1.  StatefulSet Conformance test:
    
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] StatefulSet [k8s.io] Basic StatefulSet functionality [StatefulSetBasic] Burst scaling should run to completion even with unhealthy pods [Slow] [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/statefulset.go#L687-L722)
        
        -   createAppsV1NamespacedStatefulSet
        -   deleteAppsV1NamespacedStatefulSet
        -   listAppsV1NamespacedStatefulSet
        -   readAppsV1NamespacedStatefulSet
        -   replaceAppsV1NamespacedStatefulSet
        
        [e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] StatefulSet [k8s.io] Basic StatefulSet functionality [StatefulSetBasic] Scaling should happen in predictable order and halt if any stateful pod is unhealthy [Slow] [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/statefulset.go#L577-L613e2)
        
        -   createAppsV1NamespacedStatefulSet
        -   deleteAppsV1NamespacedStatefulSet
        -   listAppsV1NamespacedStatefulSet
        -   readAppsV1NamespacedStatefulSet
        -   replaceAppsV1NamespacedStatefulSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] StatefulSet [k8s.io] Basic StatefulSet functionality [StatefulSetBasic] should have a working scale subresource [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/statefulset.go#L839-L872)
        
        -   createAppsV1NamespacedStatefulSet
        -   deleteAppsV1NamespacedStatefulSet
        -   listAppsV1NamespacedStatefulSet
        -   readAppsV1NamespacedStatefulSet
        -   readAppsV1NamespacedStatefulSetScale
        -   replaceAppsV1NamespacedStatefulSet
        -   replaceAppsV1NamespacedStatefulSetScale
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] StatefulSet [k8s.io] Basic StatefulSet functionality [StatefulSetBasic] should perform canary updates and phased rolling updates of template modifications [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/statefulset.go#L307-L488)
        
        -   createAppsV1NamespacedStatefulSet
        -   deleteAppsV1NamespacedStatefulSet
        -   listAppsV1NamespacedStatefulSet
        -   readAppsV1NamespacedStatefulSet
        -   replaceAppsV1NamespacedStatefulSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] StatefulSet [k8s.io] Basic StatefulSet functionality [StatefulSetBasic] should perform rolling updates and roll backs of template modifications [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/statefulset.go#L296-L300)
        
        -   createAppsV1NamespacedStatefulSet
        -   deleteAppsV1NamespacedStatefulSet
        -   listAppsV1NamespacedStatefulSet
        -   readAppsV1NamespacedStatefulSet
        -   replaceAppsV1NamespacedStatefulSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] StatefulSet [k8s.io] Basic StatefulSet functionality [StatefulSetBasic] Should recreate evicted statefulset [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/statefulset.go#L729-L830)
        
        -   createAppsV1NamespacedStatefulSet
        -   deleteAppsV1NamespacedStatefulSet
        -   listAppsV1NamespacedStatefulSet
        -   readAppsV1NamespacedStatefulSet
        -   replaceAppsV1NamespacedStatefulSet

3.  Replicaset

    Untested Endpoints:
    
    -   patchAppsV1NamespacedReplicaSet
    -   replaceAppsV1NamespacedReplicaSet
    
    -   listAppsV1ReplicaSetForAllNamespaces
    -   deleteAppsV1CollectionNamespacedReplicaSet
    
    -   patchAppsV1NamespacedReplicaSetScale
    -   readAppsV1NamespacedReplicaSetScale
    -   replaceAppsV1NamespacedReplicaSetScale
    
    -   patchAppsV1NamespacedReplicaSetStatus
    -   readAppsV1NamespacedReplicaSetStatus
    -   replaceAppsV1NamespacedReplicaSetStatus
    
    1.  ReplicaSet Conformance tests:
    
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] Garbage collector should orphan RS created by deployment when deleteOptions.PropagationPolicy is Orphan [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apimachinery/garbage_collector.go#L506-L558)
        
        -   listAppsV1NamespacedReplicaSet
        -   readAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] ResourceQuota should create a ResourceQuota and capture the life of a replica set. [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apimachinery/resource_quota.go#L421-L458)
        
        -   createAppsV1NamespacedReplicaSet
        -   deleteAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment deployment should delete old replica sets [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/deployment.go#L116-L134)
        
        -   createAppsV1NamespacedReplicaSet
        -   listAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment deployment should support proportional scaling [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/deployment.go#L142-L155)
        
        -   listAppsV1NamespacedReplicaSet
        -   readAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment deployment should support rollover [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/deployment.go#L126-L134)
        
        -   createAppsV1NamespacedReplicaSet
        -   listAppsV1NamespacedReplicaSet
        -   readAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment RecreateDeployment should delete old pods and create new ones [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/deployment.go#L107-L110)
        
        -   listAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment RollingUpdateDeployment should delete old pods and create new ones [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/deployment.go#L99-L101)
        
        -   createAppsV1NamespacedReplicaSet
        -   listAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment should run the lifecycle of a Deployment [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/deployment.go#L163-L463)
        
        -   listAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] ReplicaSet should adopt matching pods on creation and release no longer matching pods [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/replica_set.go#L114-L117)
        
        -   createAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] ReplicaSet should serve a basic image on each replica with a public image [Conformance] ](https://github.com/kubernetes/kubernetes/blob/1ea29cec9c923f18774092df9c3b7d0de7a193c2/test/e2e/apps/replica_set.go#L94-L97)
        
        -   createAppsV1NamespacedReplicaSet
        
        [e2e.test/v1.20.0 (linux/amd64) kubeReplicaSets to verify preemption running pathrnetes/7566c9b &#x2013; [sig-scheduling] SchedulerPreemption [Serial] PreemptionExecutionPath runs ReplicaSets to verify preemption running path [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/scheduling/preemption.go#L533-L671)
        
        -   createAppsV1NamespacedReplicaSet
        -   readAppsV1NamespacedReplicaSet

### "Scale" endpoints for Deployment, Statefulset & Replicaset<a id="sec-1-0-2"></a>

Endpoints repeat across these families and test methods for endpoints could likely be applied to similar endpoints. One expample is the "Scale" endpoints.

-   patchAppsV1NamespacedDeploymentScale
-   readAppsV1NamespacedDeploymentScale
-   replaceAppsV1NamespacedDeploymentScale

-   patchAppsV1NamespacedStatefulSetScale

-   patchAppsV1NamespacedReplicaSetScale
-   readAppsV1NamespacedReplicaSetScale
-   replaceAppsV1NamespacedReplicaSetScale

The Scale endoints use 3 verbs, patch, read & replease. Looking at Statefulset the verbs read and replace is aready covered by this [test](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/statefulset.go#L839-L872) The statefulsetScale group is only missing a conformance test for patchAppsV1NamespacedStatefulSetScale. If the Conformance is update to cover all 3 &#x2026;Scale endpoints, it is likely the same methods could be applied to Deployment and Replicaset resources.

1.  ControllerRevision Endpoints

    The ControllerRevision endpoints is the endoints group with the least conformance cover, one endpoint listAppsV1NamespacedControllerRevision is which seem to be incidentally touched by this [test](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/daemon_set.go#L357-L407).
    
    All these endpoint remain without conformance tests:
    
    -   createAppsV1NamespacedControllerRevision
    -   deleteAppsV1NamespacedControllerRevision
    -   patchAppsV1NamespacedControllerRevision
    -   readAppsV1NamespacedControllerRevision
    -   replaceAppsV1NamespacedControllerRevision
    -   listAppsV1ControllerRevisionForAllNamespaces
    -   deleteAppsV1CollectionNamespacedControllerRevision

2.  Daemonset Endpoints

    There is 11 endpoints in the family of which 6 is touched by 5 Conformance test in with a varying levels of success: [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Daemon set [Serial] should retry creating failed daemon pods [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/daemon_set.go#L277-L350)
    
    -   deleteAppsV1NamespacedDaemonSet
    -   listAppsV1NamespacedDaemonSet
    -   readAppsV1NamespacedDaemonSet
    
    [2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Daemon set [Serial] should rollback without unnecessary restarts [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/daemon_set.go#L415-L485)
    
    -   deleteAppsV1NamespacedDaemonSet
    -   listAppsV1NamespacedDaemonSet
    -   readAppsV1NamespacedDaemonSet
    -   replaceAppsV1NamespacedDaemonSet
    
    [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Daemon set [Serial] should run and stop complex daemon [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/daemon_set.go#L177-L220)
    
    -   deleteAppsV1NamespacedDaemonSet
    -   listAppsV1NamespacedDaemonSet
    -   patchAppsV1NamespacedDaemonSet
    -   readAppsV1NamespacedDaemonSet
    
    [e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Daemon set [Serial] should run and stop simple daemon [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/daemon_set.go#L149-L169)
    
    -   deleteAppsV1NamespacedDaemonSet
    -   listAppsV1NamespacedDaemonSet
    -   readAppsV1NamespacedDaemonSet
    
    and update strategy is RollingUpdate [e2e.test/V.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Daemon set [Serial] should update pod when spec was updated and update strategy is RollingUpdate [Conformance] ](https://github.com/kubernetes/kubernetes/blob/master/test/e2e/apps/daemon_set.go#L357-L407)
    
    -   deleteAppsV1NamespacedDaemonSet
    -   listAppsV1NamespacedDaemonSet
    -   patchAppsV1NamespacedDaemonSet
    -   readAppsV1NamespacedDaemonSet
    
    The following endpoint still remain without conformance tests:
    
    -   patchAppsV1NamespacedDaemonSetStatus
    -   readAppsV1NamespacedDaemonSetStatus
    -   replaceAppsV1NamespacedDaemonSetStatus
    
    -   listAppsV1DaemonSetForAllNamespaces
    
    -   deleteAppsV1CollectionNamespacedDaemonSet
    
    1.  Deployment Conformance tests:
    
        Hyperlinks not added as most of the Deployment endpoints is covered. e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] listing mutating webhooks should work [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] listing validating webhooks should work [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] patching/updating a mutating webhook should work [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] patching/updating a validating webhook should work [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should be able to deny attaching pod [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should be able to deny custom resource creation, update and deletion [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should be able to deny pod and configmap creation [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should deny crd creation [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should honor timeout [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should include webhook resources in discovery documents [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should mutate configmap [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should mutate custom resource [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should mutate custom resource with different stored version [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should mutate custom resource with pruning [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should mutate pod and apply defaults after mutation [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should not be able to mutate or prevent deletion of webhook configuration objects [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] AdmissionWebhook [Privileged:ClusterAdmin] should unconditionally reject operations on fail closed webhook [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] Aggregator Should be able to support the 1.17 Sample API Server using the current Aggregator [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] CustomResourceConversionWebhook [Privileged:ClusterAdmin] should be able to convert a non homogeneous list of CRs [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] CustomResourceConversionWebhook [Privileged:ClusterAdmin] should be able to convert from CR v1 to CR v2 [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] Garbage collector should delete RS created by deployment when not orphaning [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   listAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-api-machinery] Garbage collector should orphan RS created by deployment when deleteOptions.PropagationPolicy is Orphan [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1NamespacedDeployment
        -   listAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment deployment should delete old replica sets [Conformance] createAppsV1NamespacedDeployment
        
        -   listAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment deployment should support proportional scaling [Conformance] createAppsV1NamespacedDeployment
        
        -   listAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        -   replaceAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment deployment should support rollover [Conformance] createAppsV1NamespacedDeployment
        
        -   listAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        -   replaceAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment RecreateDeployment should delete old pods and create new ones [Conformance] createAppsV1NamespacedDeployment
        
        -   listAppsV1NamespacedDeployment
        -   readAppsV1NamespacedDeployment
        -   replaceAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment RollingUpdateDeployment should delete old pods and create new ones [Conformance] createAppsV1NamespacedDeployment
        
        -   listAppsV1NamespacedDeployment readAppsV1NamespacedDeployment
        
        e2e.test/v1.20.0 (linux/amd64) kubernetes/7566c9b &#x2013; [sig-apps] Deployment should run the lifecycle of a Deployment [Conformance] createAppsV1NamespacedDeployment
        
        -   deleteAppsV1CollectionNamespacedDeployment
        -   listAppsV1DeploymentForAllNamespaces
        -   listAppsV1NamespacedDeployment
        -   patchAppsV1NamespacedDeployment
        -   patchAppsV1NamespacedDeploymentStatus
        -   readAppsV1NamespacedDeploymentStatus
        -   replaceAppsV1NamespacedDeployment
