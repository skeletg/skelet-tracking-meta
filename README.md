# skelet-tracking-meta

> **In development.** Built from the vendor's documentation and tested against recorded requests, but not yet run
> against a production account. Don't rely on it in production until it has been verified, and expect changes.

A [Skelet](https://github.com/skeletg/skelet) tracking destination that sends shop events to Meta's Conversions API
(Facebook, Instagram), server to server. Events share their id with a browser pixel, so if you run both, Meta counts
each event once.

Events go only for shoppers who granted ads consent. Skelet's event names map to Meta's standard events:

| Skelet | Meta |
|---|---|
| `page_view` | `PageView` |
| `view_item` | `ViewContent` |
| `add_to_cart` | `AddToCart` |
| `begin_checkout` | `InitiateCheckout` |
| `add_payment_info` | `AddPaymentInfo` |
| `purchase` | `Purchase` |
| `sign_up` | `CompleteRegistration` |
| `add_to_wishlist` | `AddToWishlist` |
| `search` | `Search` |
| `generate_lead` | `Lead` |

An event Meta has no standard event for isn't sent. Email and phone are hashed the way Meta specifies before they
leave the shop.

## Install

There are no releases yet, so install from `main`:

```bash
skelet cli plugin add github.com/skeletg/skelet-tracking-meta@main
```

Then rebuild the backend and add the destination under **Marketing → Tracking** in the dashboard.

## Settings

| Setting | What |
|---|---|
| Pixel ID | The dataset (pixel) the events belong to |
| Access token | Events Manager → the dataset → Settings → Conversions API → Generate access token |
| Test event code | From Events Manager → Test events, while setting up. Events then show there and nowhere else. Leave it empty in production |

## Develop

```bash
go test ./...
```

## License

GPL-3.0, see [LICENSE](LICENSE).
