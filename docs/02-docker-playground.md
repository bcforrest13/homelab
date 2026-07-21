# Docker Playground — Session Notes

**Date:** 2026-07-21  
**Goal:** Hands-on container muscle memory — build, inspect, persist, network, destroy.

---

## Steps Completed

### 1. nginx hello world
```bash
docker run -d --name test-nginx -p 8081:80 nginx:latest
curl -I http://localhost:8081/
```
**Outcome:** HTTP 200, nginx 1.31.3, container healthy.

### 2. Inspect everything
```bash
docker ps
docker logs test-nginx --tail 20
docker inspect test-nginx
```
**Outcome:** Clean startup; bridge network `172.17.0.2`; port `8081->80/tcp`; storage via `overlayfs`; no volumes mounted.

### 3. Persist data with a volume
```bash
docker volume create myvol
docker run --rm -v myvol:/data alpine touch /data/hello.txt
docker run --rm -v myvol:/data alpine ls -la /data/
```
**Outcome:** `hello.txt` was still there in a second container — volume persistence confirmed.

### 4. Custom bridge networking
```bash
docker network create mynet
docker run -dit --name alpine1 --network mynet alpine sh
docker run -dit --name alpine2 --network mynet alpine sh
docker exec alpine1 ping -c 2 alpine2
```
**Outcome:** 0% packet loss; `alpine2` resolved to `172.19.0.3`; custom bridge DNS working.

### 5. Tear it all down
```bash
docker rm -f test-nginx alpine1 alpine2
docker volume rm myvol
docker network rm mynet
docker ps -a
docker volume ls
```
**Outcome:** All playground resources removed. Only `kanboard` remains.

---

## Quick Reference

| Concept | Confirm |
|---------|---------|
| Run detached | `docker run -d ...` |
| Publish port | `-p host:container` |
| Inspect JSON | `docker inspect <name>` |
| Persistent volume | `docker volume create ...` + `-v vol:/path` |
| Custom network DNS | containers resolve by name on same `--network` |
| Clean up | `docker rm -f`, `docker volume rm`, `docker network rm` |

---

## Next Steps
- Hook this into `~/docker/stacks/` as the next reusable stack template.
- Optional follow-up: Dockerfile for a tiny custom web app.
