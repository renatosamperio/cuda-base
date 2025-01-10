# How to build it?
To build use the following command:
```
docker buildx build  -t renatosamperio/cuda-base:latest --platform linux/amd64,linux/arm64 --build-arg CUDA_VERSION=12.5.1 --build-arg CUDA_DISTR=devel --build-arg CUDA_OS_VERSION=ubuntu24.04 -f $1/build/Dockerfile . 
```

# How to load it?
To use it locally use the following command:
```
docker buildx build  -t renatosamperio/cuda-base:latest --build-arg CUDA_VERSION=12.5.1 --build-arg CUDA_DISTR=devel --build-arg CUDA_OS_VERSION=ubuntu24.04 -f $1/build/Dockerfile . --load 
```

# How to push it?
To use it locally use the following command:
```
docker buildx build  -t renatosamperio/cuda-base:latest --platform linux/amd64,linux/arm64 --build-arg CUDA_VERSION=12.5.1 --build-arg CUDA_DISTR=devel --build-arg CUDA_OS_VERSION=ubuntu24.04 -f $1/build/Dockerfile . --push
```