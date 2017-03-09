# Install services
```sh
docker network create 'gitlab'
docker-compose up -d
```

# Register runner
Wait a moment until the gitlab service started. Then execute following command to register the node6 runner to gitlab service.
```sh
docker exec gitlab-runner \
    gitlab-runner \
    register -n \
             --name "node6" \
             --tag-list "node,node6" \
             --docker-image "node:6"
```
You can use above command to register multiple runner instance in this docker container.

# Usage
Access to http://localhost. Default user name is `root`, and the default password is `xA123456`
