---
layout: blog
title: "Tenor API Goes Private"
date: 2026-07-06
---

On January 13, 2026, Google officially announced the complete discontinuation of the public Tenor API[^1].

New Tenor integrations and API key registrations were halted that same day, setting a deadline for the end of third-party support on June 30, 2026.

## June 27, 2026
This week, Microsoft silently rolled out an update to the Windows 11 built-in GIF picker[^2], dropping Tenor entirely and swapping its backend provider to GIPHY.

It was a stark confirmation to me that Google was making no concessions, not even for the widely used operating system.

Major social hubs and communication platforms followed suit, transitioning to alternative providers prior to the deadline:
- **WhatsApp & X:** Migrated to GIPHY.
- **Bluesky:** Migrated to KLIPY.
- **Stoat:** Transitioned to their own community-driven alternative known as Gifbox[^3].

### The walled garden
This mass migration wasn't because Tenor as a platform was shutting down, but rather because Google decided to close its gates.

While third-party developers such as I were cut off, the Tenor API continues to function within the Google ecosystem.

Tenor's massive library would soon be solely reserved for Google's ecosystem, continuing to power Gboard, Google Messages, alongside Tenor's website and applications.

## June 30, 2026
The official deadline arrived.

I expected a clean, immediate blackout on all APIs.
Instead, the shutdown proved somewhat confusing.

While some legacy endpoints on `api.tenor.com/v1` immediately died, returning a termination message:
```json
{"code": 7, "error": "Tenor API is discontinued. Learn more at https://tenor.com/gifapi"}
```
A plethora of public API keys for `tenor.googleapis.com/v1` and `/v2` remained largely functional.

I refactored Fluent GIF Picker's Tenor implementation to target a few reliable endpoints that were found while shifting through network requests,
keeping the Tenor provider operational for the time being.

### Public outrage

By then, most major platforms had finalized their migrations, the sudden absence of Tenor triggering widespread user backlash across online communities.

Frustrated by less relevant search results provided by the new providers, missing favourite GIFs, and the abrupt disappearance of Tenor from all platforms.
Social media platforms such as Reddit and Twitter were quickly flooded with complaints from users confused and outraged at Google's decision to discontinue the public Tenor API.
Many mourned the loss of their favourite GIFs, having to re-upload their media to other providers.

## July 2, 2026
The hammer finally came down for the API keys.

Almost every remaining public API key across both V1 and V2 APIs was revoked.
Microsoft's SwiftKey Keyboard and Windows API keys were not spared either.

Fluent GIF Picker's Tenor implementation remained operational nonetheless.

### Is the end of Tenor around the corner?
This discontinuation of the public Tenor API feels like an incredibly short-sighted move by Google.
With the complete isolation of Tenor to the Google ecosystem, Google is effectively cutting off the platform's oxygen.

Without third-party apps driving user engagement, Tenor uploads will inevitably halt, eventually turning Tenor into a stagnant archive.

### Zombie keys
A bizarre twist occurred late into that day. I was running checks to catalog the error responses returned by the dead keys.

To my astonishment, they started to respond with valid JSON payloads.
The revoked V1, V2, and legacy keys were suddenly operational once more.

Did Google double down under pressure from major partners and public outcry?

## July 3, 2026
The hope was short-lived.

By the next morning, most of the keys were dead for good, returning a termination message:
```json
{
  "error": {
    "code": 403,
    "message": "Tenor API is discontinued. Learn more at https://developers.google.com/tenor",
    "status": "PERMISSION_DENIED"
  }
}
```

## July 5, 2026
Interestingly, while loading endpoints with the remaining valid keys in a browser triggers the standard termination message, the keys aren't entirely dead.

Passing the appropriate request headers and parameters will cause the API to deliver a valid response.

## Alternatives
The vacuum left behind by Tenor triggered an notable shift in the GIF market.

Three alternatives have risen from the aftermath, the first capable of challenging GIPHY's near-monopoly:

### KLIPY
Founded in 2021 by Frank Nawabi, one of Tenor's original co-founders, KLIPY recently emerged as the premier drop-in replacement for independent applications, being incredibly popular within developer circles.

- **Ease of Migration:** The platform was designed specifically to attract migrating developers with a near identical response structure similar to Tenor[^4], minimizing code refactoring and simplifying migration.
- **Uncensored Content:** Much like Tenor, KLIPY avoids over-sanitizing or aggressively censoring its library, allowing newer memes and internet humour typically blocked by GIPHY.
- **Entirely Free:** Currently, KLIPY provides a free service with no usage restrictions whatsoever. While this makes it an incredibly attractive alternative for open source and independent projects that are unable to afford GIPHY's enterprise pricing, it is highly unlikely to remain this way in the near future.
- **Advertisements:** KLIPY operates on an ad-supported model to cover its infrastructure costs, allowing developers to display ad placements and receive a share of the profit[^5]. However, this model may not be particularly attractive for most platforms. Integrating third-party ads into a clean search feed can potentially lead to a degraded user experience and a damaged brand image. I certainly do not desire Fluent GIF Picker to be plastered full of commercials nor my users to be bombarded by cascades of advertisements.

Personally, I surmise that their completely free model will not last long.

While KLIPY's ad-reliant model may have sustained the platform over the past 5 years when it was relatively unknown,
the massive post-Tenor influx of traffic would tip the balance.

If many implementing platforms choose to avoid the ad placements in their integrations,
KLIPY could face an uphill battle attempting to balance ballooning server expenses with ad revenue.

This opens up two possibilities for the future of KLIPY.

It could be a classic market penetration strategy:
keeping the service entirely free to capture the largest possible market share while taking on short-term debts,
and then introduce paid tiers and usage limits down the line once developers are fully locked into their ecosystem.

Alternatively, it may simply be that their infrastructure is highly optimized and cost-effective.

Only time will tell, whether KLIPY's completely free model can endure this sudden spike in demand.

### Heypster
Launched from France in 2021, Heypster is a privacy-centric GIF service serving as an alternative to GIPHY and Tenor.

- **Privacy-friendly:** Unlike GIPHY and Tenor which tracks user interaction and stores metrics for targeted advertising. Heypster operates with zero trackers and zero data collection[^7], making it compliant with both **General Data Protection Regulation (GDPR)** and the **European Digital Services Act (DSA)**[^8].
- **Ease of Migration:** Heypster provides a direct drop-in API replacement primarily for GIPHY while Tenor implementations may require additional adjustments to suffice.[^9]
- **Content Deficit:** Heypster's library leaves much to be desired. It feels severely outdated, isolated, and stale, lacking the contemporary humour typically found within popular GIF platforms.
- **Rudimentary Search:** Heypster's search engine can be unreliable, struggling to interpret queries and user intent. As such, if a query does not match an existing tag in their library, it returns empty-handed. Where most platforms would have little to no trouble providing a catalog of related results from queries such as `Hello World` and `Consuming`, Heypster yields nothing.

### Gifbox
Recently announced by the developers of Stoat, Gifbox is a brand-new GIF service developed out of necessity subsequent to the discontinuation of the public Tenor API[^3].

- **Early Infancy:** The service is still in its active development phase.
- **Ease of Migration:** Similar to KLIPY, Gifbox provides a drop-in API replacement for Tenor with their Compatibility API[^6].
- **Lack of Information:** Because the platform is so new, details regarding API rate limits and pricing tiers have yet to be revealed.

Currently, I am holding off on adding Gifbox as a GIF provider within Fluent GIF Picker until the platform matures and provides more details regarding their API.

## Fluent GIF Picker
While major social hubs and communication platforms have forsaken their Tenor support, you don't have to give up on your favourite Tenor library just yet. 

**Fluent GIF Picker** still fully supports Tenor post-shutdown.
The app provides you with ad-free, continued, uninterrupted access to Tenor's massive library.

If you want to keep using Tenor alongside KLIPY, GIPHY, and other providers on Windows, you can simply select the Tenor GIF provider within the app's settings.

👉 [Get Fluent GIF Picker from Microsoft Store](https://apps.microsoft.com/detail/9n6q7kzx4ngj)

Themed | Customizable |
:-----:|:------------:|
![](https://store-images.s-microsoft.com/image/apps.19137.14009613241251235.83df3984-172d-4e06-af85-9bcc212b4614.36695eed-571d-4c2a-be79-f97463dfcfb5)  |  ![](https://store-images.s-microsoft.com/image/apps.7016.14009613241251235.83df3984-172d-4e06-af85-9bcc212b4614.1fd4b031-453f-4898-b261-3ec4d7d0d07b)

---
### Footnotes
[^1]: [Discontinuation of Tenor API service for app developers](https://support.google.com/tenor/answer/10455265#whatll-happen-to-the-tenor-api&zippy=%2Cwhatll-happen-to-the-tenor-api)
[^2]: [Windows 11 Insider Experimental Preview Build 26300.8687 - Windows Insider Program \| Microsoft Learn](https://learn.microsoft.com/en-us/windows-insider/release-notes/experimental/preview-build-26300-8687)
[^3]: [Introducing Gifbox, the new GIF sharing service from Stoat - Stoat](https://stoat.chat/updates/introducing-gifbox)
[^4]: [Migrate from Tenor - KLIPY API \| GIF API & Stickers API](https://docs.klipy.com/migrate-from-tenor)
[^5]: [Advertisements - KLIPY API \| GIF API & Stickers API](https://docs.klipy.com/advertisements)
[^6]: [heypster-gif: Compliant with GDPR and DSA unlike Giphy and Tenor-gif. \| by heypster \| Medium](https://medium.com/@heypster/heypster-gif-compliant-with-gdpr-and-dsa-unlike-giphy-and-tenor-gif-3e7f544cca10)
[^7]: [Compatibility API - Overview - Gifbox Docs](https://gifbox.me/dev/docs/compat/overview)
[^8]: [heypster-gif: Why you should not integrate a GIF API that tracks your users. \| by heypster \| Medium](https://medium.com/@heypster/why-you-should-not-integrate-a-gif-api-that-tracks-your-users-69012446dfae)
[^9]: [heypster-gif: Easy migration from Giphy or Tenor to heypster. \| by heypster \| Medium](https://medium.com/@heypster/easy-migration-from-giphy-or-tenor-to-heypster-0be2ffec6a6a)