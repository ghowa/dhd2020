# Repository for the Workshop "Deep Learning and Visual Media", Tue 3 March 2020, DHd 2020
## Installation

0. Clone this repository and enter folder (or download, extract and enter folder):
```
git clone https://github.com/ghowa/dhd2020.git
```
```
cd dhd2020
```
1. Create virtual environment to make sure we don't mess with your system python install and install all needed packages:

If you have a Conda python install, try this:
```
conda create --nsame detectron2
```
```
conda activate detectron2
```
Or try this: https://medium.com/deepvisionguru/how-to-embed-detectron2-in-your-computer-vision-project-817f29149461

For vanilla python, try this:
```
python -m venv detectron2
```
```
source detectron2/bin/activate
```
```
pip install -r detectron2/requirements.txt
```
2. Install precompiled Detectron with CPU support only:
```
pip install detectron2 -f https://dl.fbaipublicfiles.com/detectron2/wheels/cpu/index.html
```
OR: Install precompiled Detectron for CUDA 10.1:
```
pip install detectron2 -f https://dl.fbaipublicfiles.com/detectron2/wheels/cu101/index.html
```  
3. Create a new Jupyter kernel which uses the virtual environment you have just created:
```
ipython kernel install --user --name=detectron2
```
4. Download Labelme2COCO converter and make it executable:
```
curl -JLO https://raw.githubusercontent.com/wkentaro/labelme/master/examples/instance_segmentation/labelme2coco.py
```
```
chmod 700 labelme2coco.py
```

## Try out pretrained models

1. Copy your sample images to dhd2020/input

2. Run the following network from Detectron's model zoo:
```
python detectron2/demo.py --config-file detectron2/lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-PanopticSegmentation/panoptic_fpn_R_101_3x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-PanopticSegmentation/panoptic_fpn_R_101_3x/139514519/model_final_cafdb1.pkl
```
Other interesting models:
```
python detectron2/demo.py --config-file detectron2/lib/python3.7/site-packages/detectron2/model_zoo/configs/Cityscapes/mask_rcnn_R_50_FPN.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://Cityscapes/mask_rcnn_R_50_FPN/142423278/model_final_af9cf5.pkl
```
```
python detectron2/demo.py --config-file detectron2/lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x.yaml   --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-InstanceSegmentation/mask_rcnn_R_50_FPN_3x/137849600/model_final_f10217.pkl
```
```
python detectron2/demo.py --config-file detectron2/lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-Detection/faster_rcnn_R_101_FPN_3x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-Detection/faster_rcnn_R_101_FPN_3x/137851257/model_final_f6e8b1.pkl
```
```
python detectron2/demo.py --config-file detectron2/lib/python3.7/site-packages/detectron2/model_zoo/configs/COCO-Keypoints/keypoint_rcnn_R_101_FPN_3x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS detectron2://COCO-Keypoints/keypoint_rcnn_R_101_FPN_3x/138363331/model_final_997cc7.pkl
```
```
python detectron2/demo.py --config-file detectron2/lib/python3.7/site-packages/detectron2/model_zoo/configs/LVIS-InstanceSegmentation/mask_rcnn_R_50_FPN_1x.yaml --input input/* --output output  --opts MODEL.DEVICE cpu MODEL.WEIGHTS  detectron2://LVIS-InstanceSegmentation/mask_rcnn_R_50_FPN_1x/144219072/model_final_571f7c.pkl
```

## Analysis

Run Jupyter notebook
```
jupyter notebook
```
Open deep_watching.ipynb and make sure the 'detectron2' kernel is used


## Annotate

1. Copy training images to train/ and test images to test/

2. Add your own categories to the text file 'labels'

3. Run Labelme
```
labelme train/ --labels labels
```
```
labelme test/ --labels labels
```
4. Convert into COCO json
```
./labelme2coco.py --labels labels train/ train-coco/
```
```
./labelme2coco.py --labels labels test/ test-coco/
```
5. Test annotations in Jupyter notebook
Run Jupyter notebook
```
jupyter notebook
```
Open coco_test.ipynb and make sure the 'detectron2' kernel is used

## Train

1. Create yaml for Detectron2 

2. Register custom train/test set to Detectron2

3. Run training
