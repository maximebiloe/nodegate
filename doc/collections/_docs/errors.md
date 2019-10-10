---
layout: documentation
title: Errors
---

# Errors

The class `PipelineError` allows modifiers to return a contextualized error to the pipeline executor.
This error extends the default Node.js `Error` object.

## Properties

### container

Container state before the error.

### response

If applicable: the response for the last executed request.

## Methods

### constructor(message, [response])

Constructor of the `PipelineError`.

_Arguments_

| Argument | Type       | Description                      |
| :------- | :--------- | :------------------------------- |
| message  | **string** | **Required.** Error explanation. |
| response | **object** | Last request response.           |

_Example_

```js
new PipelineError('Invalid request', {
  statusCode: 500,
  body: {
    reason: 'Missing parameter: param',
  },
});
```

### setContainer(container)

Set the last state of the container to the error.

_Arguments_

| Argument  | Type       | Description                     |
| :-------- | :--------- | :------------------------------ |
| container | **object** | **Required.** Container to set. |

_Example_

```js
const error = new PipelineError('Invalid request');
error.setContainer({
  statusCode: 400,
  body: {
    reason: 'Missing parameter: param',
  }
});
```