# Functions
>Helps to transform the supplied values in a way that makes it more useable to us.

[Go Template Language](https://golang.org/pkg/text/template/)

[Sprig Functions](https://masterminds.github.io/sprig/)

[Specialized Functions](https://helm.sh/docs/howto/charts_tips_and_tricks/)

`- name: {{ quote .Chart.Name }}`{{copy}}

`- name: {{ upper .Chart.Name }}`{{copy}}

# Pipelines
>way of getting several things done in sequence

`- name: {{ .Chart.Name | upper | quote }}`{{copy}}

`- name: {{ .Chart.Name | default "KF-Chart" | quote }}`{{copy}}

[See More About Functions](https://helm.sh/docs/chart_template_guide/functions_and_pipelines/)

# Function Controls
>Provides ability to control the flow of a template's generation.

1. if/else for creating conditional blocks
2. with to specify a scope
3. range, which provides a "for each"-style loop

`touch kingfisher-chart/templates/configmap.yaml`{{execute}}

ConfigMap file `kingfisher-chart/templates/configmap.yaml`{{open}}

<pre class="file" data-filename="configmap.yaml" data-target="replace">
apiVersion: v1
kind: ConfigMap
metadata:
  name: {{ .Release.Name }}-configmap
data:
  envType: {{ .Values.config.envType | default "QA" | upper | quote }}
  {{ if eq .Values.config.envType "qa" }}
  sizeLimit: 1Gi
  {{ end }}
</pre>

Custom Values file `kf-custom-values.yaml`{{open}}

<pre class="file" data-filename="kf-custom-values.yaml" data-target="append">

config:
  envType: "qa"
</pre>


Package
`helm package kingfisher-chart`{{execute}}

Dry Run
`helm install kingfisher-chart-0.1.0.tgz --name kingfisher -f kf-cusom-values.yaml --dry-run --debug `{{execute}}

- Controlling Spaces
> {{- (with the dash and space added) indicates that whitespace should be chomped left, while -}} means whitespace to the right should be consumed

<pre class="file" data-filename="configmap.yaml" data-target="replace">
apiVersion: v1
kind: ConfigMap
metadata:
  name: {{ .Release.Name }}-configmap
data:
  envType: {{ .Values.config.envType | default "QA" | upper | quote }}
  {{- if eq .Values.config.envType "QA" }}
  sizeLimit: 1Gi
  {{- end }}
</pre>

Package
 `helm package kingfisher-chart`{{execute}}

Dry Run
`helm install kingfisher-chart-0.1.0.tgz --name kingfisher -f kf-cusom-values.yaml --dry-run --debug `{{execute}}
