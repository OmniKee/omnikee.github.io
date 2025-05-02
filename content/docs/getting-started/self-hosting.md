+++
title = "Self-hosting"
description = "Running OmniKee as a Docker container on your own infrastructure"
draft = false
weight = 30
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "If you like, you can host OmniKee on your own server. Since OmniKee is a static web application without a server component, just serving the HTML, CSS, and JavaScript will do."
toc = true
top = false
+++

# Docker

Serve OmniKee on port 8080:

```bash
docker run \
    --name omnikee \
    -p  8080:8080 \
    ghcr.io/omnikee/omnikee
```

The [BusyBox `httpd` server](https://www.busybox.net/downloads/BusyBox.html#httpd) is very minimalistic - there will be no log messages to indicate the server is running.

You can alternatively provide a version number matching a release, e.g. `ghcr.io/omnikee/omnikee:v0.1.36`

