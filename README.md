# nifi-protobuf-processor [![codecov](https://codecov.io/gh/whiver/nifi-protobuf-processor/branch/master/graph/badge.svg)](https://codecov.io/gh/whiver/nifi-protobuf-processor) [![Build Status](https://travis-ci.org/whiver/nifi-protobuf-processor.svg?branch=master)](https://travis-ci.org/whiver/nifi-protobuf-processor)
An Apache NiFi processor to encode and decode data using Google Protocol Buffers schemas.

## Features

As this processor is a work-in-progress, the features already implemented and tested are checked.

### Main functionalities
- [x] Graphical configuration interface in Apache NiFi
- [ ] Encode a raw payload to Protocol Buffers
- [x] Decode a Protocol Buffers payload to JSON
- [ ] Support dependencies in proto files
- [ ] Allow to encode/decode from/to XML, JSON, YAML

### Protobuf schema specification
- [x] Support compiled schema at a specified user location on the disk
- [ ] Support compiled schema embedded in the flowfile
- [ ] Support embedding raw .proto files in the flowfile

### Processor packaging
- [ ] Provides a ready-to-use Docker image of Apache NiFi with the NiFi Protobuf Processor

## Installation

### Using a stable release
Grab the latest release directly from the releases page and copy the `.nar` file in the Apache NiFi `lib` folder.

### Building the latest version
Clone this project and build the processor `nar` file using Maven:

    mvn nifi-nar:nar
    
Then simply copy the generated `nar` file into the Apache NiFi `lib` folder.


## Usage

See the installation section to learn how to integrate this processor in Apache NiFi.
This projects add 2 different new processors in NiFi:

- `ProtobufDecoderProcessor`, which **decodes** a Protobuf-encoded payload to different kind of structured formats ;
- `ProtobufEncoderProcessor`, which **encodes** a payload in a structured format using a Protobuf schema.

These processors both expect the incoming flowfiles to have the `protobuf.schemaPath` defined, which should contain the
path to the compiled `.desc` proto file to use to decode/encode the data.

For now, the only structured format the processors can process is the JSON. In the future, there should be more formats
available (XML and YAML are expected).