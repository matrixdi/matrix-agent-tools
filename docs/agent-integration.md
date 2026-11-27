# Matrix Agent Tools - Autonomous Agent Integration

## Commercial environment

Matrix Agent Tools provides a limited Base Mainnet commercial release using USDC (eip155:8453).

Five offline analysis products are released, subject to current pricing and admission availability. Deployment Guard and protected live network operations remain held.

## Discover

Remote MCP endpoint:

https://agents.matrixdigitalltd.com/v1/agent/mcp

Transport: Streamable HTTP.

Initialize the MCP connection and discover current tools using tools/list. Inspect the actual tool input schemas.

Live catalogue:

https://agents.matrixdigitalltd.com/v1/agent/catalog

Buyer manifest:

https://agents.matrixdigitalltd.com/v1/agent/buyer-client.json

The live catalogue is authoritative for supported routes, pricing and availability.

## Authenticate and quote

Follow the wallet-enrollment instructions in the current buyer manifest and catalogue.

Machine jobs do not require a human subscription.

An enrolled agent can request a quotation using:

    POST /v1/agent/quotes
    Authorization: Bearer <machine-token>
    Content-Type: application/json

Supply the documented route, payload and a persistent idempotency_key.

Keep machine credentials and wallet private keys in a secure local credential store. Never transmit a private key to the service.

Validate quotation ownership, product, payload, amount, currency, expiry and payment resource against the agent's authorized spending policy.

## Default payment protocol

The default is the server-reserved nonce workflow.

Use the supported buyer client and validate the complete HTTP 402 payment requirements before signing.

Persist the exact authorization and idempotency key. Submit Payment-Signature using the documented request contract.

## Optional buyer v1.2.0

Download:

https://agents.matrixdigitalltd.com/clients/matrix-agent-tools/1.2.0/matrix-agent-tools-buyer-1.2.0.zip

Documentation:

https://agents.matrixdigitalltd.com/clients/matrix-agent-tools/1.2.0/QUOTE-PROOF.md

The optional standard_quote_proof_v1 mode requires the following:

1. Obtain an authenticated extended-mode quotation.
2. Validate and sign the payment locally.
3. Durably persist the signed payment envelope.
4. Register the signed quotation commitment without transmitting Payment-Signature.
5. Require the documented successful commitment-registration response.
6. Transmit the exact original payment authorization.
7. Recover payment and execution status.

Do not regenerate the authorization, nonce or idempotency key to recover uncertain delivery.

## Settlement and execution recovery

An HTTP 202 response indicates that processing or reconciliation may remain pending.

Use the authenticated status URL associated with the original quotation. A pending response does not authorize a second payment.

Final payment verification and job completion are separate states.

## Limitations

The optional extension requires Matrix-specific integration. Unmodified generic x402 compatibility and third-party Bazaar acceptance are not claimed.

Extended-mode live settlement remains uncertified.

Always consult the live catalogue before making a purchase.

No protected live network route should be treated as commercially available until explicitly released.
