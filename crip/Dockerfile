FROM tensorflow/tensorflow:1.15.2-gpu-py3

RUN pip install --upgrade pip setuptools Cython opencv-python


WORKDIR /
RUN apt update && apt install -y git build-essential libgl1-mesa-glx curl
RUN git clone https://github.com/qhgz2013/anime-face-detector.git
RUN git clone https://github.com/GitHub30/gdrive.sh.git && cd gdrive.sh && curl gdrive.sh | bash -s 1WjBgfOUqp4sdRd9BHs4TkdH2EcBtV5ri
RUN mv gdrive.sh/res101_faster_rcnn_iter_60000.zip . && unzip res101_faster_rcnn_iter_60000.zip && mv res101_faster_rcnn_iter_60000* anime-face-detector/model


WORKDIR /anime-face-detector
RUN make clean && make

CMD python main.py -i /input -o /output/output.json
