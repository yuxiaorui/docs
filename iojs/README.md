# Supported tags and respective `Dockerfile` links

-	[`1.8.1`, `1.8`, `1` (*1.8/Dockerfile*)](https://github.com/iojs/docker-iojs/blob/4cf03be7e0b4abcd60a3a93947d9351c3b8b4be7/1.8/Dockerfile)
-	[`1.8.1-onbuild`, `1.8-onbuild`, `1-onbuild` (*1.8/onbuild/Dockerfile*)](https://github.com/iojs/docker-iojs/blob/4cf03be7e0b4abcd60a3a93947d9351c3b8b4be7/1.8/onbuild/Dockerfile)
-	[`1.8.1-slim`, `1.8-slim`, `1-slim` (*1.8/slim/Dockerfile*)](https://github.com/iojs/docker-iojs/blob/4cf03be7e0b4abcd60a3a93947d9351c3b8b4be7/1.8/slim/Dockerfile)
-	[`2.0.1`, `2.0`, `2`, `latest` (*2.0/Dockerfile*)](https://github.com/iojs/docker-iojs/blob/8caf041be35322d93ca81d214b5fc1160b348e67/2.0/Dockerfile)
-	[`2.0.1-onbuild`, `2.0-onbuild`, `2-onbuild`, `onbuild` (*2.0/onbuild/Dockerfile*)](https://github.com/iojs/docker-iojs/blob/8caf041be35322d93ca81d214b5fc1160b348e67/2.0/onbuild/Dockerfile)
-	[`2.0.1-slim`, `2.0-slim`, `2-slim`, `slim` (*2.0/slim/Dockerfile*)](https://github.com/iojs/docker-iojs/blob/8caf041be35322d93ca81d214b5fc1160b348e67/2.0/slim/Dockerfile)

For more information about this image and its history, please see the [relevant manifest file (`library/iojs`)](https://github.com/docker-library/official-images/blob/master/library/iojs) in the [`docker-library/official-images` GitHub repo](https://github.com/docker-library/official-images).

## What is io.js?

io.js is a JavaScript platform built on Chrome's V8 runtime. This project began as a fork of Joyent's Node.js™ and is compatible with the npm ecosystem.

Why? io.js aims to provide faster and predictable release cycles. It currently merges in the latest language, API and performance improvements to V8 while also updating libuv and other base libraries.

This project aims to continue development of io.js under an "open governance model" as opposed to corporate stewardship.

> [iojs.org/faq.html](https://iojs.org/faq.html)

![logo](https://raw.githubusercontent.com/docker-library/docs/master/iojs/logo.png)

# How to use this image

If you want to distribute your application on the docker registry, create a `Dockerfile` in the root of application directory:

	FROM iojs:onbuild
	
	# Expose the ports that your app uses. For example:
	EXPOSE 8080

Then simply run:

	$ docker build -t iojs-app
	...
	$ docker run --rm -it iojs-app

To run a single script, you can mount it in a volume under `/usr/src/app`. From the root of your application directory (assuming your script is named `index.js`):

	$ docker run -v "$PWD":/usr/src/app -w /usr/src/app -it --rm iojs iojs index.js

# Image Variants

The `iojs` images come in many flavors, each designed for a specific use case.

## `iojs:<version>`

This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is designed to be used both as a throw away container (mount your source code and start the container to start your app), as well as the base to build other images off of. This tag is based off of [`buildpack-deps`](https://registry.hub.docker.com/_/buildpack-deps/). `buildpack-deps` is designed for the average user of docker who has many images on their system. It, by design, has a large number of extremely common Debian packages. This reduces the number of packages that images that derive from it need to install, thus reducing the overall size of all images on your system.

## `iojs:onbuild`

This image makes building derivative images easier. For most use cases, creating a `Dockerfile` in the base of your project directory with the line `FROM iojs:onbuild` will be enough to create a stand-alone image for your project.

## `iojs:slim`

This image does not contain the common packages contained in the default tag and only contains the minimal packages needed to run `iojs`. Unless you are working in an environment where *only* the iojs image will be deployed and you have space constraints, we highly recommend using the default image of this repository.

# License

View [license information](https://github.com/iojs/io.js/blob/master/LICENSE) for the software contained in this image.

# Supported Docker versions

This image is officially supported on Docker version 1.6.2.

Support for older versions (down to 1.0) is provided on a best-effort basis.

# User Feedback

## Documentation

Documentation for this image is stored in the [`iojs/` directory](https://github.com/docker-library/docs/tree/master/iojs) of the [`docker-library/docs` GitHub repo](https://github.com/docker-library/docs). Be sure to familiarize yourself with the [repository's `README.md` file](https://github.com/docker-library/docs/blob/master/README.md) before attempting a pull request.

## Issues

If you have any problems with or questions about this image, please contact us through a [GitHub issue](https://github.com/iojs/docker-iojs/issues).

You can also reach many of the official image maintainers via the `#docker-library` IRC channel on [Freenode](https://freenode.net).

## Contributing

You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a [GitHub issue](https://github.com/iojs/docker-iojs/issues), especially for more ambitious contributions. This gives other contributors a chance to point you in the right direction, give you feedback on your design, and help you find out if someone else is working on the same thing.
