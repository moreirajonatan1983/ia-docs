# Pull Request Documentation (English)

## 🌿 Branch Name
`feature/DEV-XXXX-cross-traceability-aws-datadog`
*(Replace `XXXX` with your actual ticket ID)*

---

## 📝 Pull Request Title
`feat(observability): enable cross-traceability between AWS CloudWatch and Datadog APM`

---

## 💬 Commit Message & PR Description

**Commit Title:**
`feat(observability): correlate aws and datadog traces in mdc logs`

**Commit Body / PR Description:**
```text
Implements the setup and injection of traceability variables (Trace IDs and Span IDs) to correlate CloudWatch logs with Datadog APM in our ECS Serverless architecture.

Main changes:
- `application.yaml`: Modified the `logging.pattern` to force the printing of MDC variables `%X{dd.trace_id}`, `%X{dd.span_id}` (originated by the Datadog Java Agent), and `%X{aws.trace_id}`.
- `OptionalCompanyHeaderInterceptor.java`: Added logic to read the native AWS Ingress header (`X-Amzn-Trace-Id`) inside the `preHandle` method, injecting it into the Spring Boot MDC context as `aws.trace_id`.
- No modifications were required in the `afterCompletion` method since the pre-existing `MDC.clear()` already prevents variable leakage between threads on the embedded application server.

Infrastructure Dependency:
Ensure the ECS container starts with `-Ddd.logs.injection=true` and `-Ddd.trace.header.tags="X-Amzn-Trace-Id:aws.trace_id"` via Dockerfile (CMD) or Terraform `var.container_def` block.
```
