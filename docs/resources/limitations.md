---
sidebar_position: 50
description: Here you can learn about what might not be possible inside Power BI.
slug: /limitations
---

# Limitations

If you're serious about content, then it's recommended that you spend some time reading this page in detail to understand why the visual has challenges for some types of HTML or web-based content.

:::info A Very Quick Summary

- Microsoft hosts custom visuals in **[sandboxed iframes](https://www.w3schools.com/TAGS/att_iframe_sandbox.asp)** in order to keep a user safe from potentially malicious third-party code.
- It doesn't matter whether a custom visual is certified or uncertified when it comes to this limitation.
- Therefore some things that work in a standalone web browser or web application will nto work, no matter how hard you try, and we can't change this.

:::

## Choice of Visual Edition

In the regular edition, the visual is not certified and can handle more HTML use cases, but it does not receive certification benefits, such as export to PowerPoint or PDF. In **HTML Content (lite)**, the visual has these additional benefits, but in order to comply with certification rules, it can only handle simpler HTML use cases as the cost of more security for the report viewer.

Please refer to the [Visual Editions](visual-editions) page for more information on what HTML tags are permitted in the certified edition.

## Things "Protected" By Microsoft from Custom Visuals via Sandboxing

The visual can't handle some aspects of HTML, due to the sandboxing rules applied by Power BI's main window. [This is detailed below](#custom-visuals-high-level) if you wish to understand further, but if you're attempting any of the following, then you're probably out of luck:

- Some hyperlinks (although `http` and `https` are [supported via delegation to Power BI](properties-content-formatting#allow-opening-urls))

- `<iframe>` elements in Desktop - reports may need to be published to the Power BI Service to be tested/viewed.

- `<iframe>` elements that embed content from sites that block [cross origin resource sharing, or CORS (e.g. YouTube)](#cross-origin-resource-sharing-cors). We'll try and collect the ones we know to work [below](#embeddable-content-known-to-work).

- `<script>` tags referencing externally-hosted JavaScript.

- `<object>` tags.

- Modal windows or popups

- Cookies or local storage

:::tip There May Be Some that Work
If you find one that's not listed, [please let me know about it](https://github.com/dm-p/powerbi-visuals-html-content/issues) so I can investigate and update the documentation (or the visual, if it turns out to be a bug) accordingly.
:::
