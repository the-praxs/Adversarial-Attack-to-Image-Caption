# Adversarial-Attack-to-Image-Caption
- This project focused on creating adversarial samples to attack unknowned image-captioning models and test theirs robustness.
- Our code built on python 3.6 and PyTorch 1.10. One can check the dependencies in [requirement.txt](https://github.com/katsamapol/Adversarial-Attack-to-Image-Caption/blob/main/requirements.txt)
- The code is not working with python 3.7 and above, however, one can migrate it to python 3.7+ by changing images manipulation library from [scipy.misc.imread](https://docs.scipy.org/doc/scipy-1.1.0/reference/generated/scipy.misc.imread.html) to other newer libraries such as [imageio](https://imageio.readthedocs.io/en/v2.8.0/userapi.html). 

## Disclaimer
- We thank sgrvinod's repository [A PyTorch Totorial to Image Captioning](https://github.com/sgrvinod/a-PyTorch-Tutorial-to-Image-Captioning) for his comprehensive image-captioning tutorial.
- We thank rmokady's repository [CLIP Prefix Captioning](https://github.com/rmokady/CLIP_prefix_caption) for creating image-captioning model from CLIP.
Both incredibly inspired us to work on this topic.

## Installing Prerequisites
Make sure you have conda installed.
- [Windows](https://conda.io/projects/conda/en/latest/user-guide/install/windows.html)
- [macOS](https://conda.io/projects/conda/en/latest/user-guide/install/macos.html)
- [Linux](https://conda.io/projects/conda/en/latest/user-guide/install/linux.html)


Create new conda environment with a specified python3.6 version
```
conda create -n python=3.6 [your_environment_name]
```

Install [requirement.txt](https://github.com/katsamapol/Adversarial-Attack-to-Image-Caption/blob/main/requirements.txt) with conda install command
```
conda install --file requirements.txt
```

## Getting Data
- Download MSCOCO2014 [training](http://images.cocodataset.org/zips/train2014.zip) and [validation](http://images.cocodataset.org/zips/val2014.zip) images.
- Download captions of the images created by Andrej Karpathy and Li Fei-Fei in JSON blobs format [here](https://cs.stanford.edu/people/karpathy/deepimagesent/caption_datasets.zip).

## Data Preprocessing
In `params_class.py`
- Specify data path to your working directory e.g., `data_path = "/data/"`
- Extract Karpathy's JSON files to your working directory under caption_datasets folder i.e., `/data/caption_datasets/`
- Extract MSCOCO2014 images to your working directory under images folder i.e., `/data/images/`

Then run
```
conda activate [your_environment_name]
python create_input_files.py
```
*Don't forget to run every command inside your conda with python3.6 installed


## Training
#TODO explaning how to use train_args.py to train resnet50, resnet101, and resnet152 models
#And carify that even select "start_from_scratch" the model will still be train using pre-trained model trained on ImageNet dataset.

Check training options: 
```
python train_args.py -h
```
To begin training, you must specify 
1. which model you want to use between resnet50, resnet101, and resnet152
2. which dataset you want to use between coco2014 and flickr8k
3. begin finetuning from scratch between True and False, select False if you want to continue training from your saved model.
4. Finetune your model encode between True and False
```
python train_args.py --which_model="resnet101" --which_data="coco2014" --start_from_scratch="True" --fine_tune_encoder="True"

```
## Evaluating
#TODO Explaning how to use eval_args.py to evaluate models.

## Captioning
#TODO Explaning how to use caption_args.py to create caption from an image.

## Attacking (ResNet)
#TODO 

## Attacking (CLIP prefix captioning)
User can use adversarial images provided in the "results/perturbed-images"
Or create their own adversarial image from attack_args.py
#TODO

