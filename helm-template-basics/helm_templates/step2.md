- This object provides access to values passed into the chart

Values file `kingfisher-chart/values.yaml`{{open}}

- Order of specificity.

1. The values.yaml file in the chart
2. ###### If this is a subchart, the values.yaml file of a parent chart
3. ##### A values file if passed into helm install or helm upgrade with the -f flag
4. #### Individual parameters passed with --set

- Create Custom Values File
`touch kf-custom-values.yaml`{{execute}}

Custom Values file `kf-custom-values.yaml`{{open}}

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

`helm init`{{execute}}

Package
 `helm package kingfisher-chart`{{execute}}

Dry Run
`helm install kingfisher-chart-0.1.0.tgz --name kingfisher -f kf-cusom-values.yaml --set replicaCount=3 --dry-run --debug `{{execute}}
