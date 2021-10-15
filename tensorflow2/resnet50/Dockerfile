FROM infuseai/primehub-notebook:tensorflow-v2-6-0-248e155b

USER "jovyan"
RUN pip install tensorflow-hub && \
    python3 -c "import tensorflow as tf; \
import tensorflow_hub as hub; \
model = tf.keras.Sequential([hub.KerasLayer('https://tfhub.dev/google/imagenet/resnet_v2_50/classification/5')]); \
model.build([None, 224, 224, 3]); \
model.save('resnet_v2_50'); \
    " && \
    wget https://storage.googleapis.com/download.tensorflow.org/data/ImageNetLabels.txt -O resnet_v2_50/ImageNetLabels.txt

USER root
RUN mkdir /home/models && mv /home/jovyan/resnet_v2_50 /home/models

USER "jovyan"
