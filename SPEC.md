Spec for Matrix Stickers
====

## Sticker

A **sticker** is a reusable image that is hosted outside of matrix which can be identified by one or more aliases.

A **pack** is a collection of stickers that share a common theme.

## Events

### Message

###  uk.half-shot.sticker

This event should render a image given by the sticker name.

We use the m.image event to display it to any client supporting images BUT clients can also make
use of the unsigned data to discover and replicate the sticker.

#### Content

| Content Key  | Type         | Description |
| ------------ | ------------ | ----------- |
| body         | string       | Textual fallback in the format " %sticker_name% (%pack_name%) "
| msgtype      | string       | Always "m.image" |
| url          | resource url | The image file containing the sticker |
| info         | [Image Info](https://www.matrix.org/docs/spec/r0.0.1/client_server.html#m-image) |

#### Unsigned

| Content Key  | Type         | Description |
| ------------ | ------------ | ----------- |
| msgtype      | string       | Always "uk.half-shot.sticker" |
| pack_name    | string       | The name of the pack |
| sticker_name | string       | The name of the sticker |

```
"content":
{
  "body": " floofy fox (foxes)"
  "msgtype": "uk.half-shot.sticker"
  "url": "mxc://blahblahblah"
  "info": [Image Info]
}
"unsigned":
{
  "msgtype": "uk.half-shot.sticker"
  "pack_name": "foxes"
  "sticker_name": "floofy fox"
}
```
