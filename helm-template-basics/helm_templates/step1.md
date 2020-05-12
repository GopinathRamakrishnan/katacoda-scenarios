- Let's create a chart and tokenize further

`helm create kingfisher-chart`{{execute}}

Deployment template file `kingfisher-chart/templates/deployment.yaml`{{open}}

Values file `kingfisher-chart/values.yaml`{{open}}

A template directive is enclosed in {{ and }} blocks

Values are namespaced objects seperated by (.)

The leading dot indicates that we start with the top-most namespace for this scope

- Built in Objects

| Object Name   | Description                                                           |
|:-------------:|---------------------------------------------------------------------- |
| Release       | This object describes the release itself.                             |
| Values        | Values supplied from the defualt values.yaml file and custom supplied |
| Chart         | The contents of the Chart.yaml                                        |
| Files         | Non special files present inside the chart                            |
| Capabilities  | Provides information about what capabilities the K8s cluster supports |
|Template       | Contains information about the current template                       |
