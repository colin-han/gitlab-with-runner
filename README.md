# Install services
```sh
docker-compose up -d
```

# Register runner
Wait a moment until the gitlab service started. Then execute following command to register the node6 runner to gitlab service.
```sh
docker exec gitlab-runner-node6 gitlab-runner register -n
```

# Usage
Access to http://localhost. Default user name is `root`, and the default password is `xA123456`
