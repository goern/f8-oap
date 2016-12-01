= A Fabric8 OpenShift Authentication Proxy

== Deployment

Create a ConfigMap to be used by the application: `oc create configmape --form-file=secret/`

Deploy the proxy via `oc create -f f8-oap.yaml`

Use `oc process -v=OAUTH_CLIENT_REDIRECT_URI=`oc get route f8-oap --template='{{if .spec.tls }}https{{ else }}http{{ end }}://{{ .spec.host }}/oauth/openshift/callback'` -f oauth-client-template-yaml | oc create -f -` to create a new oauth client.
