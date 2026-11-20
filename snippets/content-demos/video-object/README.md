# VideoObject (DEMO)

A product video with thumbnail, duration and URLs.

| | |
|---|---|
| Identifier | `video-object` |
| schema.org type | [VideoObject](https://schema.org/VideoObject) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

Demo name, description, thumbnail, upload date, duration and content and embed URLs.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "VideoObject",
    "name": "Product Demo and Review",
    "description": "Watch our comprehensive product demonstration and in-depth review",
    "thumbnailUrl": "{{config.web.secure.base_url}}media/video/thumbnail.jpg",
    "uploadDate": "2024-01-15T10:00:00+00:00",
    "duration": "PT5M30S",
    "contentUrl": "{{config.web.secure.base_url}}media/video/demo.mp4",
    "embedUrl": "https://www.youtube.com/embed/example"
}
```

## Variables and directives

- `{{config.web.secure.base_url}}`: secure base URL.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "VideoObject",
    "name": "Product Demo and Review",
    "description": "Watch our comprehensive product demonstration and in-depth review",
    "thumbnailUrl": "https://www.example.com/media/video/thumbnail.jpg",
    "uploadDate": "2024-01-15T10:00:00+00:00",
    "duration": "PT5M30S",
    "contentUrl": "https://www.example.com/media/video/demo.mp4",
    "embedUrl": "https://www.youtube.com/embed/example"
}
```

## Good to know

- A demo to copy for the page that shows the video. Google needs a real, crawlable thumbnail and video URL.

_A demo template: its values are examples, not data from your store._
