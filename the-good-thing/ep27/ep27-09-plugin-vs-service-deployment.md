---
type: podcast-chunk
title: Plugin vs Dedicated Service Deployment
slug: ep27-09-plugin-vs-service-deployment
series: The Good Thing
episode: 27
chunk: 9
segment: Feature flags, local development, and deployment tradeoffs
timecode: 00:38:48 – 00:43:10
start_time: 00:38:48
end_time: 00:43:10
speakers:
  - Jesse
  - Jens
  - Dustin
  - Ludwig
topics:
  - Plugin Deployment
  - Service Deployment
  - Feature Flags
tags:
  - plugin-architecture
  - deployment
  - dev-environments
  - feature-flags
entities:
  - WunderGraph
  - Cosmo Connect
summary: Comparison of plugin deployment and dedicated services, covering local development benefits, feature flags, and tradeoffs in deployment strategy.
---


## Deployment Options and Use Cases

### Plugin Deployment Benefits
- **Local Development**: Easy to try things out quickly
- **Preview Changes**: Can deploy Cosmo Connect plugins as feature flags
- **No Router Redeployment**: Don't need to deploy another router to preview changes on QA systems
- **Code Reuse**: Same code can be converted between plugin and service by just changing the main file

### Service Deployment Benefits
- **Resource Control**: Allocate specific resources per pod/deployment
- **Platform Team Approval**: When platform teams don't want processes forked from untrusted source control
- **Infrastructure Access**: Access to VPCs, RDS, and other AWS services
- **Full Monitoring**: Use your own Prometheus, OpenTelemetry, etc.

## Feature Flag Integration

The team highlights a powerful use case with Cosmo's graph feature flags:
- Create a copy of your graph
- Replace subgraphs in the feature flag
- Deploy a plugin with mock data for new functionality
- Test in staging without heavy operations or ops involvement
- Perfect for rapid prototyping and experimentation

## Code Reusability

Ludwig emphasizes that the same codebase can be used for both:
- Plugin: Use helper to run on socket with HashiCorp go plugin
- Service: Launch standard HTTP/2 gRPC server over network

This flexibility allows teams to start with plugins for development and easily move to services for production when needed.
