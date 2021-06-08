# :sauropod: nanosaur

[![Docker Builder CI](https://github.com/rnanosaur/nanosaur/workflows/Docker%20Builder%20CI/badge.svg)](https://github.com/rnanosaur/nanosaur/actions?query=workflow%3A%22Docker+Builder+CI%22)

NanoSaur is a little tracked robot ROS2 enabled, made for an NVIDIA Jetson Nano

* Website: [nanosaur.ai](https://nanosaur.ai)
* Do you need an help? [Discord](https://discord.gg/NSrC52P5mw)
* For technical details follow [wiki](https://github.com/rnanosaur/nanosaur/wiki)
* Something wrong? Open an [issue](https://github.com/rnanosaur/nanosaur/issues)

[Nanosaur Docker hub](https://hub.docker.com/u/nanosaur)

## Install nanosaur system
```
git clone https://github.com/rnanosaur/nanosaur.git
sudo bash nanosaur/nanosaur_bringup/scripts/install.sh
```

After the installation please **reboot** the jetson board

## Run nanosaur

This script start the docker-compose

```
cd nanosaur/
docker-compose up -d
```

# Develop

This following part is to develop with nanosaur

##  Build Docker

Make ROS2 foxy jetson-container

```
git clone --branch patch-1 https://github.com/rbonghi/jetson-containers.git
./jetson-containers/scripts/docker_build_ros.sh foxy
```

After foxy build, build the nanosaur docker for jetson

```
cd nanosaur
docker build -f Dockerfile.dev -t nanosaur/nanosaur:latest .
```

## Run docker container

https://answers.ros.org/question/358453/ros2-docker-multiple-hosts/

```
docker run --runtime nvidia -it --rm  --network host --device /dev/i2c-1 -v /tmp/argus_socket:/tmp/argus_socket -v $HOME/nanosaur:/opt/ros_ws/src/nanosaur nanosaur/nanosaur:latest bash
```

# License

* All code is Under license [MIT](LICENSE)
* All stl files included in **nanosaur_description/meshes** are under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg

For more information about this project please follow [nanosaur.ai/about](https://nanosaur.ai/about/#license)