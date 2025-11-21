# Creating a High-Interaction Docker Container Image
Source: https://help.zscaler.com/deception/creating-high-interaction-docker-container-image
PDF: https://help.zscaler.com/pdf/com/en/1531450.pdf

High-interaction containers are fully interactive applications in a docker container. You must configure all the components required for the application in a single docker image, and then upload the image to the Zscaler Deception Admin Portal.
WordPress is a service that requires multiple running components, a database, and a web server.
A sample compressed file (.zip) includes the following components necessary to create a docker container that runs a WordPress instance:
- `Dockerfile`: The file used to create the docker image.
- `make-db.sh`: The script used to create the databases required by the WordPress service.
- `wp-config.php`: The WordPress configuration file.
-
`docker-entrypoint.sh`: The `ENTRYPOINT` script that runs the container when started from a docker image.
The `ENTRYPOINT` script must not exit. If it exits, the service stops.
You can download the following sample compressed (.zip) file that has all the components necessary to create a docker container that runs a WordPress instance.
[Download](/downloads/deception/miragemaker/application-datasets/creating-high-interaction-docker-container-image/wordpress.zip)
To create a docker image:
- Create a docker file and the associated configuration files that are required to configure a docker image. You can use the sample file, if required.
-
In the command prompt, navigate to the directory where you have the files, and run the following commands:
- docker build --tag <image-name> .
For example, `docker build --tag myimage .`
-  docker save wordpress:latest > <image-name>
For example, `docker save wordpress:latest > myimage`
The `<image-name>``.tar` file is created in the current directory.
-
Run the following command to compress the `<image-name>``.tar` file as a gzip file:
gzip <image-name>.tar
For example, `gzip myimage.tar`