# docker-gitlab-runner-jdk-maven3
Gitlab CI Runner Docker image with java &amp; maven installed

进入目录，将jdk的压缩文件放入dockerfile文件夹，DockerFile文件里对应的JDK名称也相应修改，最后docker-compose.yml目录运行`docker-compose build`打包镜像，该镜像可用于gitlab继承gitlab-runner,运行maven脚本打包构建java项目。
