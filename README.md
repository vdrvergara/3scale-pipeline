3scale-pipeline
---
How to use Tekton to automate API creation and update on 3Scale
---

To try out this demo you can use an application on repo https://github.com/vdrvergara/halting-shock.git and deploy it on Openshift. The instructions to deploy it are on the repo.

This demostration uses a namespace called *demo*.

 Install 3scale-toolbox to generate 3scale-toolbox remote config file. To do so, first you will have to download and install 3scale-toolbox in your machine. Reference and documentation abou 3scale-toolbox can be found [here](https://github.com/3scale/3scale_toolbox.git), and installation file to you S.O. distribution can be found [here](https://github.com/3scale/3scale_toolbox_packaging).

1. Execute 3scale command to connect to a 3scale installation

```
 3scale remote add <remote-name> https://<user-key>@<3scale-admin-URL>
```

2. Create a config map with your 3scale configuration file (.3scalerc.yaml) in your home directory.

```
  oc create configmap toolbox --from-file=$HOME/.3scale.yaml
```

3. Fill up parameters
3scale repo
https://github.com/vdrvergara/3scale-tekton-pipeline.git

App repo 
https://github.com/vdrvergara/halting-shock.git

Base url
http://halting-shock.demo.svc:8080


Prod url
http://halting-shock-demo.apps.cluster-d0cc.d0cc.sandbox825.opentlc.com/

image:
registry.redhat.io/3scale-amp2/toolbox-rhel7:3scale2.10

Account id: 2445584031479

delete PipelineRun
for i in $(oc get pr | awk '{print $1}'); do oc delete pr $i; done;

image: 'nmasse/3scale-toolbox:master'


    :endpoint: https://red-hat-vergara-admin.3scale.net

    user key 6c5812dccff9069f0ba823c207750536 


