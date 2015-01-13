# Vulcand

## install etcd

```bash
docker run -p 4001:4001 -v /etc/ssl/certs/:/etc/ssl/certs/  quay.io/coreos/etcd:v0.4.6
```


## install vulcand

```bash
docker run -d -p 80:8182 -p 8181:8181 mailgun/vulcand:v0.8.0-alpha.3 /go/bin/vulcand -apiInterface=0.0.0.0 --etcd=http://<etcd-host>:4001
```

## install vulcanctl

```bash
# install nsenter from docker instance
docker run --rm -v /usr/local/bin:/target jpetazzo/nsenter

# list processes
docker ps
# get processid for running vulcand container
docker inspect --format {{.State.Pid}} <container id>
# enter shell inside
sudo nsenter --target <processid> --mount --uts --ipc --net --pid

```

## create server and backends

### backend
```bash
vctl backend upsert -id test-node-be
```
### server
```bash
vctl server upsert -b test-node-be -id test-node-srv1 -url http://92.222.71.238:49154
```

### host
```bash
vctl host upsert --name example.com
```

### frontend
```bash
vctl frontend upsert -id test-node-fe -route='Path("/")' -b=test-node-be
vctl frontend upsert -id test-node-fe-test -route='PathRegexp("/.*")' -b=test-node-be
```
