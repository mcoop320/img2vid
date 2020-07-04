# img2vid [![npm version](https://badge.fury.io/js/img2vid.svg)](https://badge.fury.io/js/img2vid)

Generate videos or gifs from images. Includes captions, audio, transitions and zoompan.

## Requires

**[ffmpeg](http://ffmpeg.org)** with `--enable-libass`

## Install

```bash
npm install img2vid
```

## Example Usage

```js
{
  slides: [
    {
      path: 'examples/exampleData/squirrel.jpg',
      duration: 2
    },
    {
      path: 'examples/exampleData/cassettes.jpg',
      duration: 2
    },
    {
      path: 'examples/exampleData/mouse.jpg',
      duration: 2
    }
  ],
  captions: [
    {
      text: 'Img2Vid',
      start: 0,
      end: 6,
      style: {
        pos: [640, 360],
        lineAlignment: 'bottom right'
      }
    }
  ],
  width: 640,
  height: 419,
  output: 'examples/outputs/simple.webp',
  assOutput: 'examples/outputs/simple.ass',
  forceScale: true
}
```

## Options
| key        | required             | default    | type     | description                                  |
|------------|----------------------|------------|----------|----------------------------------------------|
| slides     | Y                    |            | [Object] |                                              |
| captions   | N                    |            | [Object] |                                              |
| width      | Y                    | 640        | Number   | Pixels                                       |
| height     | Y                    | 480        | Number   | Pixels                                       |
| output     | Y                    | output.mp4 | String   | filepath.[mp4/gif/webp]                      |
| forceScale | N                    | false      | Boolean  | Use if input images are different sizes      |
| duration   | N                    |            | Number   | Output Duration                              |
| assOutput  | Y iff using captions | subs.ass   | String   | ASS File Output - filepath.ass               |
| hardSub    | N                    | true       | Boolean  | Render captions over output                  |
| audio      | N                    |            | String   | Path to audio file                           |
| genpalette | N                    | false      | Boolean  | Generate color palette for Gifs/Webp outputs |
| gifLoop    | N                    | true       | Boolean  | Continually loop Gifs/Webp outputs           |
| verbose    | N                    | true       | Boolean  | Show Logs                                    |

## Slide Options
| key        | required | default | type   | description    |
|------------|----------|---------|--------|----------------|
| path       | Y        |         | String | image filepath |
| duration   | Y        | 2       | Number | Seconds        |
| transition | N        |         | Object |                |
| zoomPan    | N        |         | Object |                |

## Transition Options
| key      | required | default | type   | description               |
|----------|----------|---------|--------|---------------------------|
| type     | Y        |         | String | See available transitions |
| duration | Y        | 1       | Number | Seconds to transition     |


## ZoomPan Options
| key         | required | default | type          | description                          |
|-------------|----------|---------|---------------|--------------------------------------|
| startTime   | N        | 0       | Number        | Seconds from start of slide          |
| endTime     | Y        |         | Number        | Seconds to finish ZP                 |
| zoomStart   | N        | 1       | Number        | Scale Factor to Start                |
| zoomEnd     | Y        | 1       | Number        | Scale Factor to End                  |
| xStart      | N        | 0       | Number        | Start X Position                     |
| yStart      | N        | 0       | Number        | Start Y Position                     |
| xEnd        | Y        | 0       | Number        | End X Position                       |
| yEnd        | Y        | 0       | Number        | End Y Position                       |
| jitterScale | N        | 2       | Number\|False | Temp scale image up to reduce jitter |