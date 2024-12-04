
# [X-AnyLabeling](https://github.com/CVHub520/X-AnyLabeling) Deployment
## Quick Start
- add the raw data folder path in docker-compose.yml
```dockerfile
- type: bind # Bind mount the host directory into the container
    source: /home/yichen/datasets
    target: /root/datasets
```
- run the following command to start the docker container
```bash
git clone --recursive https://github.com/Ea510chan/anylabeling-deploy.git
cd anylabeling-deploy/docker && docker-compose up
```
## (Optional) Enable CUDA-based Inference
- **Change to GPU:** et the __preferred_device__ field to GPU in the [app_info.py](X-AnyLabeling/anylabeling/app_info.py) configuration file.

## (Optional) Export LabelMe Annotations to VOC Format
- **Export LabelMe Annotations to VOC Format**
    Use the following command to convert LabelMe annotations to VOC format:
    ```bash
    python3 anylabeling-deploy/labelme/examples/semantic_segmentation/labelme2voc.py path/to/labelme/data path/to/output/voc --labels path/to/labels.txt --noobject
    ```

## Acknowledgments
This project builds upon the excellent work done by the [X-Anylabeling](https://github.com/CVHub520/X-AnyLabeling) and [AnyLabeling](https://github.com/vietanhdev/anylabeling) team. I'm grateful for their efforts in creating a flexible and powerful labeling tool for the community.