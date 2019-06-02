# Reactronica

> Warning: Highly experimental. APIs will change.

React audio components for making music in the browser. Uses [ToneJS](https://tonejs.github.io/) under the hood.

Check out the demo:
https://unkleho.github.io/reactronica/

Strongly influenced by [React Music](https://github.com/FormidableLabs/react-music).

Check out the demo - [http://unkleho.github.io/reactronica](http://unkleho.github.io/reactronica).

[![NPM](https://img.shields.io/npm/v/reactronica.svg)](https://www.npmjs.com/package/reactronica)

## Install

```bash
npm install --save reactronica
```

## Usage

<!-- prettier-ignore-start -->
```jsx
import React, { Component } from 'react';

import { Song, Track, Instrument, Effect } from 'reactronica';

class Example extends Component {
  render() {
    return (
      <Song tempo={90} isPlaying={false}>
        <Track
          steps={[
            {
              note: 'C3',
              duration: 0.5,
            },
            {
              note: 'D3',
              duration: 0.5,
            },
            null,
            null,
          ]}
          effects={[
            <Effect type="feedbackDelay" />,
            <Effect type="distortion" />
          ]}
          // Callback for every tick
          onStepPlay={}
        >
          <Instrument type="polySynth" notes={[]} />
        </Track>
        <Track>
          <Instrument type="sampler" samples={{
            'C3': 'path/to/kick.mp3',
            'D3': 'path/to/snare.mp3',
            'E3': 'path/to/hihat.mp3',
          }} />
        </Track>
      </Song>
    );
  }
}
```
<!-- prettier-ignore-end -->

## Documentation

### `<Song />`

#### Props

- `tempo` (number): Speed or pace of the song. Measured in beats per minute.
- `isPlaying` (bool): Whether the song is playing or not. Defaults to `false`.

### `<Track />`

#### Props

- `steps` (array)
- `effects` (array)
- `onStepPlay` (func): Called on every tick.

### `<Instrument />`

#### Props

- `type` (string)
- `notes` (array)

## Development

```bash
# Start Reactronica component build watch
$ npm start
# To run example page, in new terminal:
$ cd example
$ npm start
# If you get a babel-eslint issue, create a .env file with SKIP_PREFLIGHT_CHECK=true in ./example
```

## Known Bugs

- If you get `Hooks can only be called inside the body of a function component.`, have a look at https://github.com/facebook/react/issues/14721. Try going into the examples folder and running `npm link ../node_modules/react`.
- If multiple effects are added, effects don't update unless they are removed in the order they are added. Could be an issue with `[...prevState.effects, effect]`.

## Thanks

- https://tonejs.github.io/
- https://github.com/FormidableLabs/react-music
- https://github.com/transitive-bullshit/create-react-library
- https://github.com/crabacus/the-open-source-drumkit for the drum sounds

## License

MIT © [unkleho](https://github.com/unkleho)