---
id: metric-formats
title: Metrics Formats
sidebar_label: Metrics Formats
description: Sumo Logic supports the Graphite, Carbon 2.0, and Prometheus metric formats.
---

Sumo supports the Graphite, Carbon 2.0, and Prometheus metric formats. 

## Graphite

Graphite metrics are formatted like this:

```
metric_path metric_value metric_timestamp
```

Where:

* `metric_path` is a dot-separated string that identifies the thing being measured.
* `metric_value` is any numeric value.
* `metric_timestamp` is a UNIX timestamp.

Here’s an example of a graphite metric:  

```
cluster-1.node-1.cpu-1.cpu-idle 97.29 1460061337
```

In the metric above: 

* The thing being measured is `cluster-1.node-1.cpu-1.cpu-idle`, which we could colloquially refer to as the `cpu-idle` value for cpu-1, in node-1, in cluster-1.  
* The value measured is 97.29.
* The timestamp for the instant that the metric was measured is 1460061337.

:::tip
Graphite does not support meta tags. However, you can use Sumo's metric rules editor to tag metrics with key-value pairs derived from a Graphite metric’s metric_path. Then, you can use those key-value pairs in metric queries. For more information, see [About Metric Rules](docs/metrics/metric-rules-editor#about-metric-rules).
:::

## Carbon 2.0

Carbon 2.0 metrics conform to the [Metrics 2.0](http://metrics20.org/) specification.

Carbon 2.0 metrics look like this:

```
intrinsic_tags meta_tags value timestamp
```

:::tip
There are two spaces between `intrinsic_tags` and `meta_tags`. If a tag is listed before the double space, then it is an intrinsic tag. If a tag is listed after the double space, then it is a meta tag.
:::

Where:

* `intrinsic_tags` is one or more space-separated key-value pairs that uniquely identify what is being measured and are metric identifiers. Intrinsic tags are also referred to as dimensions. If you have two data points sent with same set of dimension values then they will be values in the same metric time series.

    :::note
    `intrinsic_tags` must be followed by two spaces.
    :::

* `meta_tags` is zero or more space-separated key-value pairs that provide additional, but not identifying information about the thing being measured. A meta tag is a piece of metadata that might be useful in querying your metrics. It doesn’t identify the thing being measured, but provides additional information of interest. Meta tags are meant to be used in addition to intrinsic tags so that you can more conveniently select the metrics. For example, it might be interesting to know the collection agent that obtained the measurement. 
* `value` is any numeric value.
* `timestamp` is a UNIX timestamp.

In the Graphite-formatted metric described above, the bit that identifies the thing being measured—the `metric_path`—is:

```
cluster-1.node-1.cpu-1.cpu-idle
```

In the Carbon 2.0 format, that metric_path translates to a set of intrinsic tags:

```
cluster=cluster-1 node=node-1 cpu=cpu-1 metric=cpu_idle
```

Carbon 2.0 is a richer metric format than Graphite, because it supports meta tags. So, a Carbon 2.0-formatted version of our example metric could include additional key-value pairs that will make our metrics easy to query. For example, below we include a meta tag that identifies the agent that collected the metric.

```
cluster=cluster-1 node=node-1 cpu=cpu-1 metric=cpu_idle  agent=biggie <value> <timestamp>
```

The following is an example of `intrinsic_tags` with an agent
`meta-tags`, a value, and a timestamp:

```
cluster=cluster-1 node=node-1 cpu=cpu-1 metric=cpu_idle agent=biggie 97.29 1460061337
```

And an example of empty set of meta tags and two spaces between the
intrinsic tags and value with timestamp :

```
cluster=cluster-1 node=node-1 cpu=cpu-1 metric=cpu_idle 97.29 146006133
```

This [blog post](https://www.sumologic.com/blog/intrinsic-vs-meta-tags/) provides additional examples and discussion.

## Prometheus

In the [Prometheus](https://prometheus.io/) format, a time series is uniquely identified by its metric name and a set of labels, which are key-value pairs. It's formed like this:

```
# HELP metric_name metric_description
# TYPE metric_name metric_type
metric_name labels value timestamp
metric_name labels value timestamp
```

Here is an example of a Prometheus metric exposition for two time series. The process of making metrics available to Prometheus is called *exposition*.

```
# HELP http_requests_total The total number of HTTP requests.
# TYPE http_requests_total counter
http_requests_total{method="post",code="200"} 1027 1395066363000
http_requests_total{method="post",code="400"}    3 1395066363000
```

See the table below for descriptions of the components of a Prometheus metric exposition.

| Component | Description |
|--|--|
| `metric_name` | Specifies the general feature of a system that is measured. For example: `http_requests_total` |
| `metric_description` | An arbitrary description or category for the metric. For example: `requests` |
| `metric_type` | the type of the metric, one of `counter`, `gauge`, `histogram`, `summary`, or `untyped`.
| `labels` | Zero or more space-separated key-value pairs that identify a particular dimensional instantiation of the metric, for example: `http_requests_total{method="post",code="200"} 1027 1395066363000`<br/>
`http_requests_total{method="post",code="400"}    3 1395066363000` |
| `value` | Value of the metric. |
| `timestamp` | The time the metric was collected, in int64 format.  |

The Prometheus format does not support metadata in the format itself. You can attach metadata to Prometheus metrics by specifying it the HTTP header when you upload the metrics to Sumo. For more information, see [Upload Metrics to an HTTP Source](docs/send-data/hosted-collectors/http-source/upload-metrics.md).
