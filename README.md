3scale Tekton Pipeline
---
How to use Tekton to automate API creation and update on 3Scale
---

To try out this demo you can use an application on [repo](https://github.com/vdrvergara/halting-shock.git} and deploy it on Openshift. The instructions to deploy this application can be found in README.md.

This demostration uses a namespace called *demo*.

1. Create namespace demo

```
oc new-project demo
```

2. Install 3scale-toolbox to generate 3scale-toolbox remote config file. To do so, first you will have to download and install 3scale-toolbox in your machine. Reference and documentation abou 3scale-toolbox can be found [here](https://github.com/3scale/3scale_toolbox.git), and installation file to you S.O. distribution can be found [here](https://github.com/3scale/3scale_toolbox_packaging). Execute 3scale command to connect to a 3scale installation:

```
 3scale remote add <remote-name> https://<user-key>@<3scale-admin-URL>
```

3. Create a config map with your 3scale configuration file (.3scalerc.yaml) in your home directory. Or change values in file cm-toolbox.yaml and apply to demo namespace.

```
  oc create configmap toolbox --from-file=$HOME/.3scale.yaml
```

4. Fill up required parameters

```
  Parameter: service-system-name
  Description: Service System name
  
  Parameter: remote
  Description: 3Scale remote name given to generate 3scalerc.yaml.
  
  Parameter: base-url
  Description: API Service Base URL.

  Parameter: prod-url
  Description: Production Service URL
  
  Parameter: context-dir
  Description: Directory to clone application code.

  Parameter: swagger-file
  Description: Name of swagger file that contains remote configuration
  
  Parameter: verbose
  Description: Debug script
    
  Parameter: account
  Description: Account ID
     
  Parameter: app-plan-name
  description: Application Plan name

  Parameter: service-id
  Description: Service ID
  
  Parameter: app-name
  description: Application name  
```

5. Create resources in Openshift

```
oc apply -f 3scale/
oc apply -f tasks/
```
  


