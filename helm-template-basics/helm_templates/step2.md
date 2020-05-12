- This object provides access to values passed into the chart

Values file `kingfisher-chart/values.yaml`{{open}}

- Order of specificity.

The values.yaml file in the chart
###### If this is a subchart, the values.yaml file of a parent chart
##### A values file if passed into helm install or helm upgrade with the -f flag
#### Individual parameters passed with --set

- Create Custom Values File
`touch kf-custom-values.yaml`{{execute}}

<pre class="file" data-filename="kf-custom-values.yaml" data-target="replace">
replicaCount: 2
resources:
  limits:
    cpu: 200m
    memory: 200Mi
  requests:
    cpu: 200m
    memory: 200Mi
</pre>

- Let's test the priority
`helm package kingfisher-chart`{{execute}}

`helm install kingfisher-chart-0.1.0.tgz --name kingfisher --dry-run --debug `{{execute}}
