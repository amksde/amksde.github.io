---
# This is a reference file only. It is outside content/, so Hugo will not publish it.
title: "Image component examples"
---

# Image component examples

Put image files in `static/images/`. A file at
`static/images/trips/udaipur-lake.jpg` is available in Markdown as
`/images/trips/udaipur-lake.jpg`.

Use the `figure` shortcode for one image with a caption:

```md
{{< figure
  src="/images/trips/udaipur-lake.jpg"
  alt="Sunset over Lake Pichola in Udaipur"
  caption="Evening at Lake Pichola."
>}}
```

Use `gallery` and `gallery-image` for a responsive image grid. The caption
belongs to the full grid:

```md
{{< gallery caption="Three moments from the Udaipur trip." >}}
  {{< gallery-image
    src="/images/trips/udaipur-lake.jpg"
    alt="Sunset over Lake Pichola"
  >}}
  {{< gallery-image
    src="/images/trips/udaipur-palace.jpg"
    alt="City Palace viewed from the lake"
  >}}
  {{< gallery-image
    src="/images/trips/udaipur-street.jpg"
    alt="A narrow street in Udaipur"
  >}}
{{< /gallery >}}
```

Always replace the example paths and write useful `alt` text that describes
the image for readers who cannot see it. Captions are optional for a single
image and the gallery, but `alt` text should always be supplied.
