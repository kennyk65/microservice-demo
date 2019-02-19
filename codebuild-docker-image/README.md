This folder contains the Dockerfile used to create the image used by Codebuild.

Ordinarily, if one wants to do a Java / Maven build, we simply use the aws/codebuild/eb-java-8-amazonlinux-64:2.4.3 image or something.  If we want to do a Docker build, we use aws/codebuild/docker:17.09.0 or something.  The problem is if we want to do a Java/Maven build, then package it with Docker.  that would require two separate CodeBuild steps.  Ugh.

So it makes sense to have an image that can do both.  The folder here contains the original Dockerfile from https://github.com/aws/aws-codebuild-docker-images, but with a few extra RUN commands near the end for installing Java 8 and Maven.

Build this with docker build -t dockerplusjdk8 .
Tag this with docker tag dockerplusjdk8:latest kennyk65/dockerplusjdk8:latest
Push to DockerHub with docker push kennyk65/dockerplusjdk8:latest

