# Upgrading from 7.2 to 7.4

Version 7.3x is deemed "transitional" and is 100% backwards-compatible with 7.2 clients.  Clients should stop using deprecated fields right away before they are removed in upcoming version 7.4.

## Changes

### Deprecating SKU Codes

The use of internal Stock Keeping Unit (SKU) codes is being replaced with EDI-friendly codes designed not to vary over time.  Two types of codes are available:

#### Extended ID

Recommended.  These codes include characters `[A-Z0-9-]` (uppercase alphanumeric, plus dash) for up to 30 characters.  Their format is fairly legible as a product code and a list of optional attributes, for example a 5000 T-shirt in navy XXL could be `5000-2XL-NVY`.

#### Compact ID

Applications which cannot handle our Extended IDs may use our Compact IDs instead, which include characters `[A-Z0-9]` (pure uppercase alphanumeric) for exactly 8 characters.  For example: `G00FYZ6H`.

### Deprecated Fields

* `Subproduct.sku` — Use `Subproduct.eid` or `Subproduct.cid`
* `Product.sku` — Use `Product.eid` or `Product.cid`
* `Product.related_skus` — Use `Product.related_eids` or `Product.related_cids`
* `ProductRequest.inventory` — Use `ProductRequest.stock`
* `ProductResponse.inventory`
* `OrderDraft.Line.sku` — Use `OrderDraft.Line.edi` or `OrderDraft.Line.cid`

### New Types

* `IdType` — An `enum` to distinguish requests by EID vs CID.

### New Fields

* `Subproduct.eid` — Replaces `sku`
* `Subproduct.cid` — Replaces `sku`
* `Product.eid` — Replaces `sku`
* `Product.cid` — Replaces `sku`
* `ProductRequest.stock` — Replaces `inventory` and specifies which of EID or CID to use in response.
* `ProductResponse.stock` — Replaces `inventory`, details quantity available per EID or CID.
* `OrderDraft.Line.eid` — Replaces `sku`
* `OrderDraft.Line.cid` — Replaces `sku`

### New Order Status

* `Shipment` — Courier-specific tracking information
* `InvoiceRequest.get_status` — Takes a list of order IDs and returns a list of `OrderConfirmation`
