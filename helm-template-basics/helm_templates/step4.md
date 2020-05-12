# Named Templates

```
{{ define "MY.NAME" }}
  # body of template here
{{ end }}
```
 - _ Files
 >Assumed to not have a k8s manifest inside. These files are not rendered to Kubernetes object definitions, but are available everywhere within other chart templates for use.

 `kingfisher-chart/templates/_helpers.tpl`{{open}}

 Deployment template file `kingfisher-chart/templates/deployment.yaml`{{open}}

 - template Function

 `name: {{ template "kingfisher-chart.fullname" . }}-deployment`{{copy}}

 - include Function

 `name: {{ include "kingfisher-chart.fullname" . | indent 2 }}`{{copy}}


- Scope should be passed to named templates
