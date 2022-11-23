+++
title = "Elasticsearch installation"
author = ["r_hasan"]
description = "installation processes on different operating systems, docker. connecting kibana after a successfull installation."
date = 2022-11-23T00:00:00+06:00
tags = ["installation"]
draft = false
+++

> download elasticsearch tar file from <https://www.elastic.co/downloads/elasticsearch> extract the folder and rename the folder to elasticsearch.
>
> download kibana tar file from <https://www.elastic.co/downloads/kibana>, extract the folder and rename to kibana.


## Common procedures {#common-procedures}

```bash
cd elasticsearch
bin/elasticsearch # and this will start elasticsearch
```

when starting elasticsearch on the terminal, all the logs will be shown where password for elasticsearch, http ca certificate and jwt to connect to kibana will be provided there.
if these credentials somehow lost or not saved by you, these can be regenerated with the following commands. another thing, the provided jwt will be valid only for 30 minute
exact after when it was generated.

```bash
bin/elasticsearch-reset-password -u elastic
bin/elasticsearch-create-enrollment-token --scope kibana
```

> Data is encrypted when being transferred within elasticsearch itself and also when we communicate with elasticsearch over http.


## Mac specific settings {#mac-specific-settings}

```bash
# cd to root folder under which kibana extracted folder resides
xattr -d -r com.apple.quarantine kibana # disabling gate keeper for the kibana directory
```


## Connecting to kibana {#connecting-to-kibana}

```shell
cd kibana
bin/kibana
```

after running the above commands kibana will start by showing the url on the terminal. we have to go the provided url and fill up the credentials and login.
