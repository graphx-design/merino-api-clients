# GraphX Merino API

[![license](https://img.shields.io/github/license/graphx-design/merino-api-clients.svg?style=plastic)]() [![GitHub release](https://img.shields.io/github/release/graphx-design/merino-api-clients.svg?style=plastic)]()

Documentation and sample client code for our Merino API.

## Introduction

This JSON-via-HTTPS service allows our registered users access to our product details and to place orders without using the web site per se.  If you require managing the user interface for your purchases but don't want to dive into cXML or EDI X12 support, this API is for you.

## Usage

The service is at: <https://www.gxd.ca/api/merino>

You will need the security realm and token we supplied in order to authenticate your requests.

Clients issue HTTP POST requests to that URL with content-type "application/json" containing exactly one `Message` object, to which the service will respond with a single `Message` object as well.  The definition for its structure is detailed in the file [gxd.merino.public.proto](https://github.com/graphx-design/merino-api-clients/blob/master/gxd.merino.public.proto).  Details about each individual field is documented directly in comments in this file, so please read it thouroughly.

While Protocol Buffers are used to define this exchange, **the Merino API is not a gRPC end point**.  It also does not support binary encoding, only JSON.  See <https://developers.google.com/protocol-buffers/docs/proto3#json> for how the field names translate directly to familiar JSON objects.  Note that per this spec, we accept both `snake_case` and `camelCase` property name formats, but we always emit the preferred `camelCase` while the definition file is declared in `snake_case`, for compatibility with the broadest set of implementations possible.  We also expect strings, not integers, for enumerations.

## LICENSE AND COPYRIGHT

The usage examples and client libraries provided in this repository are:

Copyright (c) 2018-2022 Graph X Design Inc. <https://www.gxd.ca/>

Distributed under the MIT (X11) License:
http://www.opensource.org/licenses/mit-license.php

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
