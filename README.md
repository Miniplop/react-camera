# React Camera [![Travis status build](https://travis-ci.org/Miniplop/react-camera.svg?branch=master)](https://travis-ci.org/Miniplop/react-camera/) [![npm version](https://badge.fury.io/js/react-camera.svg)](https://badge.fury.io/js/react-camera)

The comprehensive camera module for React. Including photographs! (videos, and barcode scanning coming soon)

## Getting started

`npm install react-camera`

or

`yarn add react-camera`

## Usage

```
import React, { Component } from 'react';
import Camera from 'react-camera';

export default class App extends Component {

  constructor(props) {
    super(props);
    this.takePicture = this.takePicture.bind(this);
  }

  takePicture() {
    this.camera.capture()
    .then(blob => {
      this.img.src = URL.createObjectURL(blob);
      this.img.onload = () => { URL.revokeObjectURL(this.src); }
    })
  }

  render() {
    return (
      <div style={style.container}>
        <Camera
          style={style.preview}
          ref={(cam) => {
            this.camera = cam;
          }}
        >
          <div style={style.captureContainer} onClick={this.takePicture}>
            <div style={style.captureButton} />
          </div>
        </Camera>
        <img
          style={style.captureImage}
          ref={(img) => {
            this.img = img;
          }}
        />
      </div>
    );
  }
}

const style = {
  preview: {
    position: 'relative',
  },
  captureContainer: {
    display: 'flex',
    position: 'absolute',
    justifyContent: 'center',
    zIndex: 1,
    bottom: 0,
    width: '100%'
  },
  captureButton: {
    backgroundColor: '#fff',
    borderRadius: '50%',
    height: 56,
    width: 56,
    color: '#000',
    margin: 20
  },
  captureImage: {
    width: '100%',
  }
};
```

## Component instance methods

You can access component methods by adding a ref (ie. ref="camera") prop to your <Camera> element, then you can use this.refs.camera.capture(cb), etc. inside your component.

#### `capture(): Promise`
