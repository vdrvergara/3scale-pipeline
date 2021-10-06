3scale-pipeline

1. Install 3scale toolbox locally
Package for installation
https://github.com/3scale-labs/3scale_toolbox_packaging/releases
Execute with podman:
https://access.redhat.com/documentation/en-us/red_hat_3scale_api_management/2.10/html-single/operating_3scale/index#installing_the_toolbox_container_image

2. Create a configmap with authentication file

oc new-project demo

oc create cm toolbox --from-file=$HOME/.3scalerc.yaml -n demo

