# TODOs

- Replace the default-http-backend container reference for ingress-nginx healthcheck
  - it serves a 404 page at / and serves a 200 on a /healthz endpoint
  - search ingress-nginx github doc for instructions
