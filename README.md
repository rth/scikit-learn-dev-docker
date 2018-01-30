# Development docker setup for scikit-learn


These dockerfiles are mostly used for development and testing.

By default, the scikit-learn `master` branch is compilied from source in a Debian unstable for the amd64 platform. Adapt the scikit-learn version (git tag), OS version / release and the [architecture](https://github.com/docker-library/official-images#architectures-other-than-amd64) as needed. 

### Dockerfiles

 * `debian/conda/Dockerfile`: source installation with dependencies installed with conda
 * `debian/apt/Dockerfile`: source installation with dependencies installed with apt and pip

### Building images

For instance,
```py

cd debian/conda/
docker build -t sklearn-debian-conda-amd64 .
```

