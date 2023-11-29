# Howto BuildConfig

## Create project
`$ oc new-project buildconfig-demo`

## Import image for node 16:
`oc import-image node:16 --from=image-registry.openshift-image-registry.svc:5000/openshift/nodejs:16-ubi8 --confirm -n buildconfig-demo`

## Create imagestream
`$ oc create imagestream demo-app`
`$ oc apply -f 02-demo-app-imagestream.yaml`

## Apply buildconfig
`$ oc apply -f 03-BuildConfig.yaml`

## Start build of BuildConfig
`$ oc start-build demo-buildconfig`

## Check logs
`$ oc logs -f build/demo-buildconfig-1`

# Run application

`$ oc new-app demo-app --name=demo-app1`
# Expose application to route
`$ oc expose service/demo-app1`

