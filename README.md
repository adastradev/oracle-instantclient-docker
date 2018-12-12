# oracle-instantclient-docker

## Table of Contents

- [What is this image?](#what-is-this-image)
- [How to use this image](#how-to-use-this-image)
  - [Create a `Dockerfile` in your project](#create-a-dockerfile-in-your-project)
- [Image Variants](#image-variants)
  - [`astradev/oracle-instantclient:<version>-lite`](#lite)
  - [`astradev/oracle-instantclient:<version>-full`](#full)
- [Volumes](#volumes)
- [License](#license)

## What is This Image

These Docker images contain combinations of the Oracle Instant Client packages.  The primary purpose is to make it easier to include Instant Client binaries in other Docker images without going through the install process. 

## How to Use This Image

### Create a Dockerfile in Your Project

```dockerfile
FROM node:8-slim

# Choose the correct version if more than one is available
ENV LD_LIBRARY_PATH /usr/lib/oracle/18.3/client64/lib

COPY --from=adastradev/oracle-instantclient:18.3-lite /usr/lib/oracle /usr/lib/oracle
COPY --from=adastradev/oracle-instantclient:18.3-lite /usr/lib64/libaio* /lib/

# Continue with Docker build
```

## Image Variants

### Lite

This image contains only the basiclite package.

### Full

This image contains these packages.

- basic
- devel
- jdbc
- odbc
- sqlplus
- tools

## Volumes

Each image contains the `admin` volume where Oracle config files can be placed.  The `TNS_ADMIN` environment variable has been set to this location.

## License
[License information](https://raw.githubusercontent.com/adastradev/oracle-instantclient-docker/master/LICENSE) for
this Docker project.
