# Matrix Agent Tools

> Professional pay-per-job services built for autonomous AI agents.

Matrix Agent Tools by Matrix Digital Ltd enables AI agents to discover specialist services, authenticate, obtain quotations, pay per job and receive structured execution results.

## Commercial availability

Five offline analysis products are released on Base Mainnet, subject to current pricing, admission availability and payment safeguards.

- Network: Base Mainnet (eip155:8453)
- Settlement asset: USDC
- Payment protocol: x402 v2 with Matrix quotation binding
- Human subscription required: No

## Service portfolio

| Product | Commercial status |
|---|---|
| Checkout Monitor | Released - offline analysis |
| Commerce Guard | Released - offline analysis |
| Ad Tracking Guard | Released - offline analysis |
| Tender Intelligence | Released - offline analysis |
| MCP Security Audit | Released - offline analysis |
| Deployment Guard | Held pending network certification |

Protected live network operations remain held.

Consult the live catalogue for current prices and availability. Portfolio descriptions are not payment offers.

## Connect via MCP

Remote endpoint:
https://agents.matrixdigitalltd.com/v1/agent/mcp

- Transport: Streamable HTTP
- Registry identity: com.matrixdigitalltd/agent-tools
- Registry version: 1.0.0

Discoverable tools include matrix_catalogue, matrix_quote and matrix_job_status.

Inspect the current tool schemas before invoking them.

[Official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers/com.matrixdigitalltd%2Fagent-tools/versions/1.0.0)

## Autonomous buyer integration

1. Discover services and pricing.
2. Complete wallet-enrolled machine authentication.
3. Request a quotation.
4. Validate the payment terms against the agent's spending policy.
5. Pay using the supported quotation-bound protocol.
6. Recover payment status and authorized execution results.

## Buyer resources

- [Live catalogue](https://agents.matrixdigitalltd.com/v1/agent/catalog)
- [Buyer manifest](https://agents.matrixdigitalltd.com/v1/agent/buyer-client.json)
- [Optional buyer v1.2.0](https://agents.matrixdigitalltd.com/clients/matrix-agent-tools/1.2.0/matrix-agent-tools-buyer-1.2.0.zip)
- [Extended payment documentation](https://agents.matrixdigitalltd.com/clients/matrix-agent-tools/1.2.0/QUOTE-PROOF.md)
- [Machine-readable discovery](agent-discovery.json)
- [Integration guide](docs/agent-integration.md)
- [AI-readable documentation](llms.txt)

The existing server-reserved nonce workflow remains the default.

The optional standard_quote_proof_v1 mode requires additional signed quotation proof and nonce pre-registration.

Unmodified generic x402 compatibility is not claimed. Actual extended-mode Mainnet settlement remains uncertified.

This repository contains public documentation, not proprietary application source code.

## Provider

Matrix Digital Ltd

https://matrixdigitalltd.com/
