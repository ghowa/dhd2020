# Repository for the Workshop "Deep Learning and Visual Media", Tue 3 March 2020, DHd 2020
## Installation

0. Clone this repository
```
git clone https://github.com/ghowa/dhd2020.git
```

1. Create virtual environment to make sure we don't mess with your system python install:
```
python -m venv dhd2020
source dhd2020/bin/activate
pip install -r dhd2020/requirements.txt
```
2. Install precompiled Detectron for CUDA 10.1:
```
pip install detectron2 -f https://dl.fbaipublicfiles.com/detectron2/wheels/cu101/index.html
```  
  OR: Install precompiled Detectron with CPU support only:
```
pip install detectron2 -f https://dl.fbaipublicfiles.com/detectron2/wheels/cpu/index.html
```
3. Create a new Jupyter kernel which uses the virtual environment you have just created:
```
ipython kernel install --user --name=dhd2020
```
4. Download Labelme2COCO converter and make it executable:
```
curl -JLO https://raw.githubusercontent.com/wkentaro/labelme/master/examples/instance_segmentation/labelme2coco.py
chmod 700 labelme2coco.py
```
5. Download Pycocotools demo notebook to check annotations:
```
curl -JLO https://raw.githubusercontent.com/cocodataset/cocoapi/master/PythonAPI/pycocoDemo.ipynb
```

## Try out pretrained models

1. Copy your sample images to dhd2020/input

2. Enter directory
```
cd dhd2020
```
3. Run one of the following networks from Detectron's model zoo:
```
python demo.py --config-file lib/python3.7/site-packages/detectron2/model_zoo/configs/Cityscapes/mask_rcnn_R_50_FPN.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://Cityscapes/mask_rcnn_R_50_FPN/142423278/model_final_af9cf5.pkl
```
```
python demo.py --config-file lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml   --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
```
```
python demo.py --config-file lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-Detection/faster_rcnn_R_101_FPN_3x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-Detection/faster_rcnn_R_101_FPN_3x/137851257/model_final_f6e8b1.pkl
```
```
python demo.py --config-file lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-Keypoints/keypoint_rcnn_R_101_FPN_3x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-Keypoints/keypoint_rcnn_R_101_FPN_3x/138363331/model_final_997cc7.pkl
```
```
python demo.py --config-file lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-PanopticSegmentation/panoptic_fpn_R_101_3x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-PanopticSegmentation/panoptic_fpn_R_101_3x/139514519/model_final_cafdb1.pkl
```
```
python demo.py --config-file lib/python3.7/site-packages/detectron2/model_zoo/configs/LVIS-InstanceSegmentation/mask_rcnn_R_50_FPN_1x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS  detectron2://LVIS-InstanceSegmentation/mask_rcnn_R_50_FPN_1x/144219072/model_final_571f7c.pkl
```

## Annotate

Enter own categories in labels.txt

## Analyse

Run Jupyter notebook
```
jupyter notebook
```
Open analyse.ipynb and make sure the 'dhd2020' kernel is used
