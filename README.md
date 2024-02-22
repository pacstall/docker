# Pacstall Docker Builder

This script helps to easily build and test Pacstall Docker images,
or pull them from upstream. Designed to be adaptable with other
Ubuntu and Debian-based Docker image builds.

```
Usage: pacstall-docker-builder [OPTIONS]

Options:

-V/-v, --version  Pacstall version and Docker image tag
                  (default: master)

-A/-a, --arch     Target architecture
                  (options: auto, all/off, arm64/aarch64, amd64/x86_64)
                  (default: all/off)

-D/-d, --distro   Specify a base distro to build image on
                  (options: ubuntu:{release}, debian:{release})
                  (default: ubuntu:latest)

-C/-c, --clean    Use --no-cache during Docker image build
                  (default: disabled)

-F/-f, --file     Create only the Dockerfile, with instructions
                  (default: prompted)

-B/-b, --build    Create both the Dockerfile and the Docker image
                  (default: prompted)

-P/-p, --pull     Pull a Docker image from the upstream registry
                  (options: --version, default: always uses --arch auto)

-T/-t, --test     Start up the image after build or pull is complete
                  (default: disabled or prompted)

-W/-w, --wipe     Hazardous: Delete all related Dockerfiles and images
                  (default: always prompted)

-H/-h, --help     Show this help message

Examples:

 pacstall-docker-builder -f

  Creates the file Dockerfile-Pacstall-master-YYYYMMDD for building the image
  pacstall/pacstall:YYYYMMDD, with instructions outputted to terminal
  on how to build and run it.

  Note: if no options are passed, this is the default function, but
  users will be prompted if they would like to build and run the image.


 pacstall-docker-builder -b -t -c -v 4.3.2 -a x86_64
    
  Builds and starts amd64/pacstall/pacstall:4.3.2 from scratch.


 pacstall-docker-builder -p -t -v latest
    
  Pulls and starts ghcr.io/pacstall/pacstall:latest.
```