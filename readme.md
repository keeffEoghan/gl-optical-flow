# `glsl-optical-flow`

Optical flow shader for WebGL - BYORenderer.

No drawing dependencies - for easier compatibility with any renderer which may rely on tracking the WebGL state (e.g: [`regl`](https://github.com/regl-project/regl/)).

[Check out the demo](http://epok.tech/glsl-optical-flow/).

## Installation

Install from [`npm`](https://www.npmjs.com/package/@epok.tech/glsl-optical-flow) using:
```bash
npm install @epok.tech/glsl-optical-flow
```
or:
```bash
yarn add @epok.tech/glsl-optical-flow
```

## Usage

[Check out the demo](http://epok.tech/glsl-optical-flow/), and its [source code](https://github.com/keeffEoghan/glsl-optical-flow/blob/master/example/):

You may use this in your own shader...
```glsl
precision highp float;

uniform sampler2D view;
uniform sampler2D past;
uniform float offset;
uniform float lambda;

varying vec2 uv;

#pragma glslify: opticalFlow = require('@epok.tech/glsl-optical-flow/index');

void main() {
    gl_FragColor = vec4(opticalFlow(uv, view, past, offset, lambda), 0.0, 1.0);
}
```

... or [the provided fragment shader](https://github.com/keeffEoghan/glsl-optical-flow/blob/master/index.frag.glsl); for direct usage (requiring `glslify`), or an instructive example.

## To-Do

- Cater for multi-frame blending, for consistency across time.
- Blur.

## See Also

Based on:
- Original use in [`tendrils`](https://github.com/keeffEoghan/tendrils).
- `ofxFlowTools` [article](https://forum.openframeworks.cc/t/ofxflowtools-optical-flow-fluid-dynamics-and-particles-in-glsl/15470) and [code](https://github.com/moostrik/ofxFlowTools).
- [`PixelFlow`](https://github.com/diwi/PixelFlow).
- [Thomas DieWald](http://thomasdiewald.com/blog/?p=2766).
- [Adam Ferriss](https://adamferriss.com/gush/).
- [`ofxMIOFlowGLSL`, based on work by Andrew Benson](https://github.com/princemio/ofxMIOFlowGLSL/blob/master/src/FlowShader.cpp).
- [`glslify`](https://github.com/glslify/glslify).
