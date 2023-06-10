# Roadmap

## Breaking Changes

### Remove CID for (sub-)products

Since all our users settled on EIDs, we intend to remove CIDs from the API, including the `ProductIDType` enum.  CIDs were created to satisfy some EDI X12 needs which did not materialize.

- [ ] Remove field `Subproduct.cid`
- [ ] Remove field `Product.cid`
- [ ] Remove field `Product.related_cids`
- [ ] Remove field `OrderDraft.Line.cid`
- [ ] Change type of field `ProductRequest.stock` to `string`
- [ ] Remove enum `ProductIDType`


## Additions

These are not currently scheduled and will only be implemented on demand.

### Get shipments since X

- [ ] Add `Shipment.order_ids` - Orders which it (partially?) fulfills
- [ ] Add `Shipment.contents` - Subproduct-qty tuples of what's in the box(es), all refs combined
- [ ] Add `ShipmentRequest` and `ShipmentResponse`

### Order as another

- [ ] Accept `OrderDraft.contact` to just contain the `Contact.id` of an existing user

