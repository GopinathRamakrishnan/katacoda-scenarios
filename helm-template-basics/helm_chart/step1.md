>Helm uses a packaging format called charts.
>A chart is a collection of files that describe a related set of Kubernetes resources.

## Chart

- Let's create a chart to review the structure and tokenize further.

`helm create kingfisher-chart`{{execute}}

- Verify the chart's structure

`ls -lha kingfisher-chart`{{execute}}

### Chart structure
```
Chart.yaml          # A YAML file containing information about the chart
LICENSE             # OPTIONAL: A plain text file containing the license for the chart
README.md           # OPTIONAL: A human-readable README file
values.yaml         # The default configuration values for this chart
values.schema.json  # OPTIONAL: A JSON Schema for imposing a structure on the values.yaml file
charts/             # A directory containing any charts upon which this chart depends.
crds/               # Custom Resource Definitions
templates/          # A directory of templates that, when combined with values,
                    # will generate valid Kubernetes manifest files.
templates/NOTES.txt # OPTIONAL: A plain text file containing short usage notes
```
