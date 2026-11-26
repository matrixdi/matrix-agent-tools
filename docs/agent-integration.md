# Matrix Agent Tools — integration for autonomous agents

**Status:** Testnet preview. Base Sepolia (eip155:84532). Mainnet payments are disabled. Not all product routes are available yet.

## Discover services

Remote MCP endpoint: `https://agents.matrixdigitalltd.com/v1/agent/mcp`

Transport: Streamable HTTP. Use an MCP client to initialize a connection and discover the current tools with `tools/list`. The service exposes `matrix_catalogue`, `matrix_quote` and `matrix_job_status`. Inspect the returned tool input schemas rather than assuming arguments.

For machine-readable service availability, use `matrix_catalogue` or:

```sh
curl -fsS --max-time 30 https://agents.matrixdigitalltd.com/v1/agent/catalogue
```

The catalogue is authoritative for supported routes, enrollment requirements, pricing and network. The [portfolio manifest](../agent-discovery.json) is a discovery aid, not a payment offer.

## Authenticate and request a quotation

Follow the enrollment instructions in the live catalogue for wallet-enrolled machine authentication. Keep the bearer token and wallet credentials in the agent's secure credential store. No human subscription is required for machine jobs.

For an enrolled agent, the HTTP quote contract is:

```http
POST /v1/agent/quotes
Authorization: Bearer <machine-token>
Content-Type: application/json
```

The JSON body contains `route`, `payload` (according to the supported route's schema), and `idempotency_key` (a unique persistent key for that logical job). Persist the key before sending the request; a lost response must not create a second chargeable job.

Use the returned quotation's payment and status URLs. Verify they point to the expected HTTPS service origin, and validate the product, amount, expiry and currency.

## Pay only for an authorized quotation

The current flow is quote-bound x402 v2. A POST to the returned payment URL with an empty JSON object and no payment signature can return HTTP 402 with the base64-encoded `PAYMENT-REQUIRED` header.

An x402-compatible payer should validate the challenge against its own spending policy, expected network, asset, merchant, amount and resource URL. Use the official SDK to sign; retain the exact authorization and durable submission record. The signed request uses the `PAYMENT-SIGNATURE` header. Never send a private key to the service.

On uncertain delivery or an HTTP 202 response, reconcile the existing quotation through its authorized status URL. Do not blindly create another quote or sign another payment. Read the final status and result; the finalized response may include `PAYMENT-RESPONSE`.

External network operations require the applicable verified target grant. Do not pay for an unavailable or held route.

## Product portfolio

See the [README](../README.md) for the six products and configured prices. Consult the live catalogue before purchase. The official MCP Registry record is [here](https://registry.modelcontextprotocol.io/v0.1/servers/com.matrixdigitalltd%2Fagent-tools/versions/1.0.0).

This guide describes the Matrix-specific quotation workflow. It does not claim generic one-request x402 Bazaar compatibility, marketplace acceptance, or mainnet availability.
