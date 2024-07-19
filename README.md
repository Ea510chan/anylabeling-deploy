
# [X-AnyLabeling](https://github.com/CVHub520/X-AnyLabeling) Deployment with LabelMe VOC Export Support
## Quick Start
- add the dataset path in docker-compose.yml
- for dependencies installation, please check the [Dockerfile_x](Dockerfile_x)
```bash
cd docker && docker-compose up
```
## Modified Features for X-AnyLabeling
- **Change to GPU:** et the __preferred_device__ field to GPU in the [app_info.py](X-AnyLabeling/anylabeling/app_info.py) configuration file.
- **Change installation url for `onnxruntime-gpu`:** Install from ORT Azure to make it compatible with the CUDA 12.X.

# AnyLabeling GPU Docker Deployment with LabelMe VOC Export Support
## Introduction
This project extends the [AnyLabeling](https://github.com/vietanhdev/anylabeling) tool by deploying it using Docker containers specifically optimized for GPU environments. Additionally, I've implemented a feature to export annotations to the VOC format using LabelMe, enhancing the interoperability with other computer vision tools and frameworks.
## Features
- **Dockerized AnyLabeling**: Simplifies the deployment of AnyLabeling using Docker, ensuring easy scalability and maintenance.
- **LabelMe to VOC Export**: Adds the capability to export annotations from LabelMe to the VOC format, which is widely used in the field of computer vision for tasks like object detection and semantic segmentation.

## Quick Start
Follow these instructions to get the AnyLabeling tool running with Docker and exporting data in VOC format:

1. **Clone the Repository**
    ```bash
    git clone git@github.com:Ea510chan/anylabeling-deploy.git
    cd anylabeling-deploy/docker
    ```

2. **Build and Run Docker Container**
    ```bash
    # add the dataset path in docker-compose.yml
    docker-compose up
    ```

3. **Export LabelMe Annotations to VOC Format**
    Use the following command to convert LabelMe annotations to VOC format:
    ```bash
    python3 anylabeling-deploy/labelme/examples/semantic_segmentation/labelme2voc.py path/to/labelme/data path/to/output/voc --labels path/to/labels.txt --noobject
    ```

## Acknowledgments
This project builds upon the excellent work done by the [AnyLabeling](https://github.com/vietanhdev/anylabeling) team. I'm grateful for their efforts in creating a flexible and powerful labeling tool for the community.