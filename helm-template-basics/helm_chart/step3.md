`helm init`{{execute}}

Let's package the chart

`helm package kingfisher-chart`{{execute}}

Debug the helm chart

`helm install kingfisher-chart-0.1.0 --dry-run --debug`{{execute}}
