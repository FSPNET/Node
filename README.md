# Node 

FSP Network Gen2 Server Infrastructure - Node.js

[![MicroBadger Size](https://img.shields.io/microbadger/image-size/fspnetwork/node.svg?style=flat-square)](https://microbadger.com/#/images/fspnetwork/node)
[![Docker Automated build](https://img.shields.io/docker/automated/fspnetwork/node.svg?style=flat-square)](https://hub.docker.com/r/fspnetwork/node/)
[![Docker Build Status](https://img.shields.io/docker/build/fspnetwork/node.svg?style=flat-square)](https://hub.docker.com/r/fspnetwork/node/)
[![GitHub](https://img.shields.io/github/license/fspnet/node.svg?style=flat-square)](https://github.com/fspnetwork/node/blob/master/LICENSE)
![Node Version](https://img.shields.io/badge/Node%20version-10.15-blue.svg?style=flat-square)

## Usage

- [`development` (Dockerfile.development)](https://github.com/FSPNet/node/blob/master/Dockerfile.development)
- [`latest`, `stable` (Dockerfile)](https://github.com/FSPNet/node/blob/master/Dockerfile)

```bash
docker run -d --restart=unless-stopped --name node --network net-fsp -v /opt/www:/usr/src/app:rw fspnetwork/node
```

## Development

```bash
docker run -t -d --name node_development -v /yourlocal:/usr/src/app:rw fspnetwork/node
```