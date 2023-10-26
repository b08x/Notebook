

https://claude.ai/chat/331f9ac5-b511-4fce-842b-ae6dfa996cbb



## when trying to build the original docker file

```
Reading package lists...
W: GPG error: https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4B469963BF863CC
E: The repository 'https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease' is no longer signed.
The command '/bin/bash -c apt-get update &&     apt-get install -y wget &&     apt-get install unzip &&     apt-get install -y libsm6 libxext6 libfontconfig1 libxrender1 libglib2.0-0 supervisor python-dev swig ssh libcap2-bin nano &&     mkdir -p /opt/aws &&     cd /opt/aws &&     wget https://s3.amazonaws.com/aws-cli/awscli-bundle.zip &&     unzip awscli-bundle.zip &&     python3 awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws &&     rm -rf awscli-bundle.zip awscli-bundle &&     pip install -U flake8 &&     pip install -U jsonschema &&     pip install opencv-python &&     pip install -U flask &&     pip install -U gunicorn &&     pip install -U gevent &&     pip install -U protobuf &&     pip install -U newrelic &&     pip install -U boto3 scipy &&     apt-get autoclean -y &&     apt-get autoremove -y &&     rm -rf /tmp/* /var/tmp/* &&     rm -rf /var/lib/apt/lists/*' returned a non-zero code: 100
ERROR: Service 'deepafx' failed to build : Build failed

```

### versioning for the future

So today I decided to try out interesting projects. 

Both projects ~2 years since last update

Since then, packages  depreciate and are no longer available. [docker - pinning versions](docker%20-%20pinning%20versions.md)