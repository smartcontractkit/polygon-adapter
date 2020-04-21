# Chainlink Polygon External Adapter

This adapter is for [Polygon.io](https://polygon.io/) and supports the conversion endpoint.

## Input params

- `base` or `from`: The asset to query
- `quote` or `to`: The currency to conver to
- `endpoint`: The endpoint to query (default: conversion)

## Output

```json
{
 "jobRunID": "1",
 "data": {
  "status": "success",
  "last": {
   "bid": 0.8131,
   "ask": 0.8133,
   "exchange": 48,
   "timestamp": 1587501544000
  },
  "from": "GBP",
  "to": "USD",
  "initialAmount": 1,
  "converted": 1.2299,
  "result": 1.2299
 },
 "result": 1.2299,
 "statusCode": 200
}
```

## Install

```bash
yarn
```

## Test

```bash
yarn test
```

## Create the zip

```bash
zip -r cl-polygon.zip .
```

## Docker

If you wish to use Docker to run the adapter, you can build the image by running the following command:

```bash
docker build . -t polygon-adapter
```

Then run it with:

```bash
docker run -p 8080:8080 -e API_KEY='YOUR_API_KEY' -it polygon-adapter:latest
```

## Install to AWS Lambda

- In Lambda Functions, create function
- On the Create function page:
  - Give the function a name
  - Use Node.js 12.x for the runtime
  - Choose an existing role or create a new one
  - Click Create Function
- Under Function code, select "Upload a .zip file" from the Code entry type drop-down
- Click Upload and select the `cl-polygon.zip` file
- Handler should remain index.handler
- Add the environment variable (repeat for all environment variables):
  - Key: API_KEY
  - Value: Your_API_key
- Save


## Install to GCP

- In Functions, create a new function, choose to ZIP upload
- Click Browse and select the `cl-polygon.zip` file
- Select a Storage Bucket to keep the zip in
- Function to execute: gcpservice
- Click More, Add variable (repeat for all environment variables)
  - NAME: API_KEY
  - VALUE: Your_API_key
