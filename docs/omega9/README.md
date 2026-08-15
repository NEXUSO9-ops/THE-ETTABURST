# Omega-9 Commercial Control Plane

## Authority

Sophia Key is the policy authority for identity, entitlement, provider authorization, step-up access, and audit requirements.

NEXUS is the execution control plane for routing, metering, quota enforcement, and provider isolation.

LEO LEO FIRESTORM is the operational audit and anomaly layer.

## Request lifecycle

1. Authenticate the principal.
2. Resolve tenant, subscription, and plan.
3. Resolve capability entitlement.
4. Ask Sophia Key for the policy decision.
5. Estimate request cost and verify available credit/overage authority.
6. Route only to an entitled provider/model/tool.
7. Record provider usage and customer charge.
8. Emit an immutable authorization and metering audit event.
9. Return the result with provenance metadata.

## Provider boundary

Customers do not receive OpenAI, Anthropic, Gemini, or MCP provider credentials. Provider credentials remain server-side and are selected by NEXUS after policy authorization.

## Free access

Free access is a platform-funded allowance. It is not unlimited upstream provider access. Once the allowance is exhausted, execution is denied or an explicitly enabled paid-overage/upgrade path is required.

## MCP security

MCP requests should be authorized at the HTTP authorization boundary and should preserve issuer and credential isolation. The 2026-07-28 MCP specification also supports gateway routing and metering using MCP method/name headers, which is compatible with NEXUS as the policy and metering gateway.

## Backengine MCP

The registry target `ai.backengine/backengine-mcp:8.1.1` is recorded as a policy-gated provider entry. The repository does not treat the registry cursor alone as proof that version 8.1.1 is installed or reachable; deployment verification remains a separate evidence state.

## Evidence state

Configuration files in this directory are canonical architecture/configuration artifacts. They do not by themselves prove production deployment, provider credentials, live billing, or live customer entitlements.
