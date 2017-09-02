# React Camera [NOT PUBLISHED YET] [![Travis status build](https://travis-ci.org/Miniplop/react-camera.svg?branch=master)](https://travis-ci.org/Miniplop/react-camera/)

The comprehensive camera module for React. Including photographs! (videos, and barcode scanning coming soon)

## Getting started

`npm --save react-camera`

## Usage

```
import React, { Component } from 'react';
import Camera from 'react-camera';

class App extends Component {

  constructor(props) {
    super(props);
    this.takePicture = this.takePicture.bind(this);
  }

  takePicture() {
    const { img } = this.refs;
    this.refs.camera.capture()
    .then(blob => {
      img.src = URL.createObjectURL(blob);
      img.onload = () => { URL.revokeObjectURL(this.src); }
    })
  }

  render() {
    return (
      <div style={style.container}>
        <Camera
          style={style.preview}
          ref="camera"
        >
          <div style={style.capture} onClick={this.takePicture}>[TAKE A PICTURE]</div>
        </Camera>
        <img ref="img" />
      </div>
    );
  }
}

export default App;

const style = {
  preview: {
    flex: 1,
  },
  container: {
    flex: 1,
    flexDirection: 'row',
  },
  capture: {
    flex: 0,
    backgroundColor: '#fff',
    borderRadius: 5,
    color: '#000',
    padding: 10,
    margin: 40
  },
};

```

## Component instance methods

You can access component methods by adding a ref (ie. ref="camera") prop to your <Camera> element, then you can use this.refs.camera.capture(cb), etc. inside your component.

#### `capture(): Promise`

## Development

### yarn

### npm (slower)
