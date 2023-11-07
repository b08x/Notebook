---
---


https://developer.hashicorp.com/terraform/tutorials/docker-get-started/install-cli

```bash

touch main.cf

terraofrm init

# apply the configuration than begin the provision
terraform apply

```

```
# main.cf

terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx"
  keep_locally = false
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "tutorial"

  ports {
    internal = 80
    external = 8000
  }
}

```

https://developer.hashicorp.com/terraform/tutorials/docker-get-started/docker-build