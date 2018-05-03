
## test server

- python 3.6.3           
- tensorflow-gpu            1.4.1 (conda)
- tensorflow-gpu-base       1.4.1
- tensorflow-tensorboard    1.5.1
- keras                     2.1.5 (pip)
- nvcc V8.0.61
- Pillow 5.1.0
- opencv-python 3.4.0.12
  - apt update && apt install -y libsm6 libxext6
  - apt-get install -y libxrender-dev
- check docker : which nvidia-docker
- ceate container : nvidia-docker run --rm -d -t -p 9990:9990 -v "$HOME/work:/root/work" --name wayne-env nvidia/cuda:14.04 zsh
- login container : docker exec -it wayne-env zsh

## Memory

```
from keras.backend.tensorflow_backend import set_session
config = tf.ConfigProto()
config.gpu_options.per_process_gpu_memory_fraction = 0.4
set_session(tf.Session(config=config))
```
