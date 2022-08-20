# Python Playwright
Base image for Python Playwright running in Docker on AMD64

## Dependencies
Extends [ubuntu:focal](https://hub.docker.com/_/ubuntu/#:~:text=20.04%2C%20focal%2D20220801%2C%20focal) 
Chosen based on [Playwright Compatability Documentation](https://playwright.dev/python/docs/docker#base-images)


## Dockerfile
```
# Ubuntu Focal is officially supported by the playwright project
# https://playwright.dev/python/docs/docker#base-images
# As of last testing 20220819 (jammy) 22.04 was failing for my use case
FROM ubuntu:focal

# Update Apt repositories
RUN apt-get update 

# Install and configure Python
RUN apt-get -y --no-install-recommends install python3 python3-pip

# Install python application dependencies
RUN pip3 install --upgrade pip
RUN pip3 install playwright
RUN playwright install
RUN playwright install-deps
```