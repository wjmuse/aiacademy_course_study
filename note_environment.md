
## test server

- python 3.6.3
- keras 2.0.8
- nvcc V8.0.61
- tensorflow 1.3.0
- Pillow 5.1.0
- opencv-python 3.4.0.12
  - apt update && apt install -y libsm6 libxext6
  - apt-get install -y libxrender-dev
- check docker : which nvidia-docker
- ceate container : nvidia-docker run --rm -d -t -p 9990:9990 -v "$HOME/work:/root/work" --name wayne-env nvidia/cuda:14.04 zsh
- login container : docker exec -it wayne-env zsh
