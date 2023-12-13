<br>
<p align="center">
<h1 align="center"><img src="assets/icon.png" align="center" width="6.5%"><strong>PointLLM: Empowering Large Language Models to Understand Point Clouds</strong></h1>
  <p align="center">
    <a href='https://runsenxu.com/' target='_blank'>Runsen Xu</a>&emsp;
    <a href='https://guanfang12.github.io/' target='_blank'>Xiaolong Wang</a>&emsp;
    <a href='https://tai-wang.github.io/' target='_blank'>Tai Wang</a>&emsp;
    <a href='http://yilunchen.com/about' target='_blank'>Yilun Chen</a>&emsp;
    <a href='https://oceanpang.github.io/' target='_blank'>Jiangmiao Pang*</a>&emsp;
    <a href='http://dahua.site/' target='_blank'>Dahua Lin</a>&emsp;
    <br>
    The Chinese University of Hong Kong&emsp;Shanghai AI Laboratory&emsp;Zhejiang University
  </p>
</p>

<p align="center">
  <a href="http://arxiv.org/abs/2308.16911" target='_**blank**'>
    <img src="https://img.shields.io/badge/arXiv-2308.16911-blue?">
  </a> 
  <a href="https://arxiv.org/pdf/2308.16911.pdf" target='_blank'>
    <img src="https://img.shields.io/badge/Paper-📖-blue?">
  </a> 
  <a href="https://runsenxu.com/projects/PointLLM" target='_blank'>
    <img src="https://img.shields.io/badge/Project-&#x1F680-blue">
  </a>
  <a href="http://101.230.144.196" target='_blank'>
    <img src="https://img.shields.io/badge/Demo-&#x1f917-blue">
  </a>
  <a href="" target='_blank'>
    <img src="https://visitor-badge.laobi.icu/badge?page_id=OpenRobotLab.pointllm&left_color=gray&right_color=blue">
  </a>
  <a href="https://openxlab.org.cn/apps/detail/openxlab-app/PointLLM" target='_blank'>
    <img src="https://cdn-static.openxlab.org.cn/app-center/openxlab_app.svg">
  </a>
</p>

## 🏠 About
<!-- ![Teaser](assets/teaser.jpg) -->
<div style="text-align: center;">
    <img src="assets/teaser.jpg" alt="Dialogue_Teaser" width=100% >
</div>
We introduce <b>PointLLM, a multi-modal large language model capable of understanding colored point clouds of objects.</b> It perceives object types, geometric structures, and appearance without concerns for ambiguous depth, occlusion, or viewpoint dependency. <b>We collect a novel dataset comprising 660K simple and 70K complex point-text instruction pairs</b> to enable a two-stage training strategy. To rigorously evaluate our model's perceptual abilities and its generalization capabilities, <b>we establish two benchmarks: Generative 3D Object Classification and 3D Object Captioning, assessed through three different evaluation methods.</b>

## 🔥 News
- [2023-12-08] We release the codes for training and PointLLM-v1.2. Please enjoy! &#x1F389;
- [2023-12-01] We have released an updated version of our paper (v2), which includes additional baseline comparisons, enhanced human-evaluation metrics, improved model performance (PointLLM-v1.2), and other refinements. Please check the updated version [here](https://arxiv.org/abs/2308.16911).
- [2023-10-18] We release our instruction-following data, including both the simple-description and complex instructions. Download [here](https://huggingface.co/datasets/RunsenXu/PointLLM).
- [2023-09-26] We release the inferencing codes with checkpoints as well as the Objaverse colored point cloud files we use. You can chat with PointLLM with your own machines.
- [2023-08-31] We release the [paper](http://arxiv.org/abs/2308.16911) of PointLLM and an online gradio [demo](http://101.230.144.196). Try it! &#x1F389;

<!-- contents with emoji -->
## 📋 Contents
- [🤖 Online Demo](#-online-demo)
- [💬 Dialogue Examples](#-dialogue-examples)
- [🔍 Overview](#-overview)
- [📦 Training and Inferencing](#-training-and-inferencing)
- [📝 TODO List](#-todo-list)
- [🔗 Citation](#-citation)
- [📄 License](#-license)
- [📚 Related Work](#-related-work)
- [👏 Acknowledgements](#-acknowledgements)

## 🤖 Online Demo
<b>PointLLM is online! Try it at [http://101.230.144.196](http://101.230.144.196) or at [OpenXLab/PointLLM](https://openxlab.org.cn/apps/detail/openxlab-app/PointLLM).</b>

You can chat with PointLLM about the models of the [Objaverse](https://objaverse.allenai.org) dataset or about your own point clouds!

Please do not hesitate to tell us if you have any feedback! 😃

## 💬 Dialogue Examples
| Dialogue 1 | Dialogue 2| Dialogue 3 | Dialogue 3
| :-: | :-: | :-: | :-: |
| <img width="100%" src="assets/dialogue_1.jpg"> |  <img width="100%" src="assets/dialogue_2.jpg"> |  <img width="100%" src="assets/dialogue_3.jpg"> | <img width="100%" src="assets/dialogue_1.jpg"> |


## 🔍 Overview

### Model
<p align="center">
  <img src="assets/model.jpg" align="center" width="100%">
</p>
The point encoder extracts features from the input point cloud and projects them to the latent space of the LLM backbone. The LLM backbone processes sequences of point tokens and text tokens, and generates the predicted tokens as the output.

### Experiment Results
#### Quantitave Comparisons with baselines.
Please refer to our paper for more results.
<p align="center">
  <img src="assets/cls_results.png" align="center" width="100%">
</p>
<p align="center">
  <img src="assets/caption_results.png" align="center" width="100%">
</p>
<b>!!!Note: Traditional metrics such as BLEU-1, ROUGE-L, and METEOR tend to favor shorter responses and may not effectively capture semantic accuracy. For a detailed discussion on this, please refer to our paper. We suggest the community not solely rely on these metrics for evaluation.</b>

#### Qualitative Comparisons with baselines.
Please refer to our paper for more results.
<p align="center">
  <img src="assets/qualitative_comparisons_v2.png" align="center" width="100%">
</p>

## 📦 Training and Inferencing
### Installation
We test our codes under the following environment:
- Ubuntu 20.04
- NVIDIA Driver: 515.65.01
- CUDA 11.7
- Python 3.10.13
- PyTorch 2.0.1
- Transformers 4.28.0.dev(transformers.git@cae78c46)

To start: 
1. Clone this repository.
```bash
git clone git@github.com:OpenRobotLab/PointLLM.git
cd PointLLM
```
2. Install packages
```bash
conda create -n pointllm python=3.10 -y
conda activate pointllm
pip install --upgrade pip  # enable PEP 660 support
pip install -e .

# * for training
pip install ninja
pip install flash-attn
```

### Data Preparation
#### Objaverse Data
1. Download the two compressed files of 660K Objaverse colored point clouds [here](https://huggingface.co/datasets/RunsenXu/PointLLM/tree/main). They require about 77GB of storage space.
2. Run the following command to merge the two files into one and uncompress it. This will produce a folder named `8192_npy` containing 660K point cloud files named `{Objaverse_ID}_8192.npy`. Each file is a numpy array with dimensions (8192, 6), where the first three dimensions are `xyz` and the last three dimensions are `rgb` in [0, 1] range.
```bash
cat Objaverse_660K_8192_npy_split_a* > Objaverse_660K_8192_npy.tar.gz
tar -xvf Objaverse_660K_8192_npy.tar.gz
```
3. In `PointLLM` folder, create a soft link to the uncompressed file in the directory.
```bash
cd PointLLM
ln -s /path/to/8192_npy objaverse_data
```

#### Instruction-Following Data
1. In `PointLLM` folder, create a directory named `anno_data`.
2. Our instruction-following data, including both the simple-description and complex instructions, can be downloaded [here](https://huggingface.co/datasets/RunsenXu/PointLLM). If you have difficulty downloading the data (e.g. network issue), please email the authors.
- The simple-description data has 660K samples and the complex instructions have 70K samples.
- Both training data are based on the Objaverse dataset.
- The complex instructions are generated with GPT-4.
3. Put the data files in the `anno_data` directory. The directory should look like this:
```bash
PointLLM/anno_data
├── PointLLM_brief_description_660K_filtered.json
├── PointLLM_brief_description_660K.json
└── PointLLM_complex_instruction_70K.json
```
4. Note, the `PointLLM_brief_description_660K_filtered.json` is filterd from `PointLLM_brief_description_660K.json` by removing the 3000 objects we reserved as the validataion set. If you want to reproduce the results in our paper, you should use the `PointLLM_brief_description_660K_filtered.json` for training. The `PointLLM_complex_instruction_70K.json` contains objects all from the training set.

### Training
#### Download the Initial LLM and Point Encoder Weights
1. In `PointLLM` folder, create a directory named `checkpoints`.
2. Download the pre-trained LLM and point encoder: [
PointLLM_7B_v1.1_init](https://huggingface.co/RunsenXu/PointLLM_7B_v1.1_init/tree/main) or [PointLLM_13B_v1.1_init](https://huggingface.co/RunsenXu/PointLLM_13B_v1.1_init/tree/main). Put them in the `checkpoints` directory.
3. Note, the above "v1.1" means we use the Vicuna-v1.1 checkpoints, and you do **not** need to download the original LLaMA weights again. 

#### Start Training
1. For stage-1 training, simply run:
```bash
cd PointLLM
scripts/train_stage1.sh
```
2. After stage-1 training, start stage-2 training:
```bash
scripts/train_stage2.sh
```

#### PointLLM-v1.1 and PointLLM-v1.2
Usually, you do not have to care about the following contents. They are only for reproducing the results in our v1 paper (PointLLM-v1.1). If you want to compare with our models or use our models for downstream tasks, please use PointLLM-v1.2 (refer to our v2 paper), which have better performance.
1. PointLLM v1.1 and v1.2 use slightly different pre-trained point encoders and projectors. If you want to reproduce PointLLM v1.1, edit the `config.json` file in the directory of initial LLM and point encoder weights, for example, `vim checkpoints/PointLLM_7B_v1.1_init/config.json`.
2. Change the key `"point_backbone_config_name"` to specify another point encoder config:
```bash
# change from
"point_backbone_config_name": "PointTransformer_8192point_2layer" # v1.2
# to
"point_backbone_config_name": "PointTransformer_base_8192point", # v1.1
```
3. Edit the checkpoint path of point encoder in `scripts/train_stage1.sh`:
```bash
# change from
point_backbone_ckpt=$model_name_or_path/point_bert_v1.2.pt # v1.2
# to
point_backbone_ckpt=$model_name_or_path/point_bert_v1.1.pt # v1.1
```

### Chatting
1. The trained model checkpoints are available [here](https://huggingface.co/RunsenXu) (including different versions of PointLLM). 
2. Run the following command to launch a chatbot using the `torch.float32` data type for chatting about 3D models of Objaverse. The model checkpoints will be downloaded automatically. You can also manually download the model checkpoints and specify their paths.
```bash
cd PointLLM
PYTHONPATH=$PWD python pointllm/eval/PointLLM_chat.py --model-path RunsenXu/PointLLM_7B_v1.2 --data-path objaverse_data --torch-dtype float32
```
3. You can also easily modify the codes for using point clouds other than those from Objaverse, as long as the point clouds input to the model have dimensions (N, 6), where the first three dimensions are `xyz` and the last three dimensions are `rgb` (in [0, 1] range). You may sample the point clouds to have 8192 points, as our model is trained on such point clouds.
4. The following table shows GPU requirements for different models and data types. We recommend using `torch.bfloat16` if applicable, which is used in the experiments in our paper.

|  Model   | Data Type | GPU Memory |
|:--------:|:---------:|:----------:|
| PointLLM-7B  | torch.float16 |    14GB    |
| PointLLM-7B  | torch.float32 |    28GB    |
| PointLLM-13B | torch.float16 |    26GB    |
| PointLLM-13B | torch.float32 |    52GB    |


## 📝 TODO List
- [x] Add inferencing codes with checkpoints.
- [x] Release instruction-following data.
- [x] Add training codes.
- [ ] Add evaluation codes.
- [ ] Add data generation codes.

## 🔗 Citation

If you find our work helpful, please cite:

```bibtex
@article{xu2023pointllm,
  title={PointLLM: Empowering Large Language Models to Understand Point Clouds},
  author={Xu, Runsen and Wang, Xiaolong and Wang, Tai and Chen, Yilun and Pang, Jiangmiao and Lin, Dahua},
  journal={arXiv preprint arXiv:2308.16911},
  year={2023}
}
```

## 📄 License
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png" /></a>
<br />
This work is under the <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.

## 📚 Related Work
Together, Let's make LLM for 3D great!
- [Point-Bind & Point-LLM](https://arxiv.org/abs/2309.00615): aligns point clouds with Image-Bind, and leverages ImageBind-LLM to reason multi-modality input without 3D-instruction data training.
- [3D-LLM](https://arxiv.org/abs/2307.12981): employs 2D foundation models to encode multi-view images of 3D point clouds.


## 👏 Acknowledgements
- [LLaVA](https://github.com/haotian-liu/LLaVA): Our codebase is built upon LLaVA.
- [Vicuna](https://github.com/lm-sys/FastChat): We use the Vicuna-7B and Vicuna-13B checkpoints.
- [Objaverse](https://objaverse.allenai.org): We use models of the Objaverse dataset for training and evaluation.
- [Cap3D](https://github.com/crockwell/Cap3D/): We use the Cap3D captioning data for our data generation.
- [ULIP-2](https://github.com/salesforce/ULIP): We use ULIP-2 for pre-training our point cloud encoder.
