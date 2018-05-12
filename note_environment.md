
## test server docker

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
- faiss 1.2.1
  - conda install faiss-gpu -c pytorch
- check docker : which nvidia-docker
- ceate container : nvidia-docker run --rm -d -t -p 9990:9990 -v "$HOME/work:/root/work" -v "/home/data/pixrs-data:/pixrs-data" --name wayne-env nvidia/cuda:14.04 zsh
- login container : docker exec -it wayne-env zsh

## Memory Uage Setting

```
from keras.backend.tensorflow_backend import set_session
config = tf.ConfigProto()
config.gpu_options.per_process_gpu_memory_fraction = 0.4
set_session(tf.Session(config=config))
```

## nvidia-smi 相關指令

數據說明：
- Fan: 風扇轉速
- Temp: 溫度
- Perf: 狀態性能，P0 - P12，P0 表示最大性能、P12 最小
常用參數：
- 持續更新：nvidia-smi -l 1
- 詳細資訊：nvidia-smi -q
