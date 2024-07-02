# OLTP Grafana local

This project contains docker-compose setup for local tests OpenTelemetry tracing. 

## Getting started

Just pull and run docker-compose.

For testing OpenTelemetry locally wou can use this setup (Opentelemetry Collector + Tempo + Grafana).

Easy start - easy development.


!!! *Supported only traces. Not supported metrics and logs.* 

### Requirements

1. Docker v4.3.0+
2. Git v2.45.0+

### How to "RUN"

1. Pull git repo
2. Run grafana + collector `./docker-compose up -d`
3. Check grafana availability http://localhost:3000/
4. Add agent (for example Java-agent https://opentelemetry.io/docs/zero-code/java/agent/)
5. Setup agent with [Config](#Config)
6. Run response/request (tracing will sent automatically)
7. Check traces: `Grafana->Explore->Search->Service Name=your-app-name->Span Name=yourmethod-name->Run query`

### Config

Default ports:
1. `grpc` : 4317
2. `http/protobuf` : 4318

Zero-code available for different [languages](https://opentelemetry.io/docs/zero-code/)

For example, we use [JavaAgent](https://opentelemetry.io/docs/zero-code/java/agent/)

- `OTEL_SERVICE_NAME`=`your-app-name`
- `OTEL_EXPORTER_OTLP_ENDPOINT`=`htt://localhost`
- `OTEL_EXPORTER_OTLP_PROTOCOL`=`http/protobuf` or `grpc`
- `OTEL_TRACES_EXPORTER`=`otlp`
- `OTEL_JAVAAGENT_DEBUG`=`false`
- `OTEL_LOGS_EXPORTER`=`none`
- `OTEL_METRICS_EXPORTER`=`none`
- `OTEL_RESOURCE_ATTRIBUTES`=`attribute=value`
