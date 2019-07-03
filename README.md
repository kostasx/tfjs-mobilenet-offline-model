![Drag Racing](tfjs-logo.png)

# tfjs-mobilenet-offline-model
This is an offline version of [MobileNet](https://github.com/tensorflow/models/blob/master/research/slim/nets/mobilenet_v1.md) pre-trained model for [TensorFlow.JS](https://www.tensorflow.org/js) for use with the Node.JS version of the library. The files residing in the models directory contain the neccessary `model.json` configuration file as well as the set of sharded weight files in binary format. 

## What is this?

This is a downloaded version of the pre-trained MobileNet model, that can be used with TensorFlow.JS library either in the browser or using Node.JS.

Instructions for downloading the mode configuration file and mode weights can be found here: http://jamesthom.as/blog/2018/08/07/machine-learning-in-node-dot-js-with-tensorflow-dot-js/

_(Scroll down until you find the `MobileNet Models` section)_

Kudos to [James Thomas](https://about.me/j_thomas)

## Where can it be used?

Check out this excellent post: [Machine Learning in Node.js With TensorFlow.js](http://jamesthom.as/blog/2018/08/07/machine-learning-in-node-dot-js-with-tensorflow-dot-js/)

## Quick Demo Setup (Node.JS)

- [Download Gist](https://gist.github.com/kostasx/1562671045aee2c0eb98363c69aecae9/archive/4cbad09afaafd7f72a65ec98074778eee0428cf6.zip)
- Unzip and `cd` to the newly created directory
- `$ npm install`
- [Download Model](https://github.com/kostasx/tfjs-mobilenet-offline-model/raw/master/models/v1_1.0_224.zip)
- Unzip model. It will create a folder: `v1_1.0_224`. Move it into your project folder.
- Download a sample image: `$ wget http://bit.ly/2JYSal9 -O panda.jpg`
- Predict: `$ node mobilenet-node.js v1_1.0_224 panda.jpg`

## Versions uploaded

- [v1_1.0_224.zip](https://github.com/kostasx/tfjs-mobilenet-offline-model/raw/master/models/v1_1.0_224.zip)

## Step-by-step process of downloading the files

`$ brew install jq`

`$ brew install parallel`

`$ curl https://storage.googleapis.com/tfjs-models/tfjs/mobilenet_v1_1.0_224/model.json > mode.json`

`$ cat model.json | jq -r ".weightsManifest[].paths[0]" | sed 's/^/https:\/\/storage.googleapis.com\/tfjs-models\/tfjs\/mobilenet_v1_1.0_224\//' |  parallel curl -O`
