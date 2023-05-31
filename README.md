# _DENOISING_OF_IMAGES_USING_SCU-NET_ARCHITECTURE






__*The following results are obtained by our SCUNet with purely synthetic training data! 
We did not use the paired noisy/clean data by DND and SIDD during training!*__
<p align="left">
  <a href="https://github.com/cszn/SCUNet">
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/input_16.gif"/>
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/cc_fnb_0042_16.gif"/>
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/ct_fnb_0019_16.gif"/>
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/cty_fnb_0047_16.gif"/>
  </a>
</p>

<p align="left">
  <a href="https://github.com/cszn/SCUNet">
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/g_fnb_0009_16.gif"/>
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/kf_fnb_0058_16.gif"/>
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/mc_fnb_0001_16.gif"/>
    <img width=48% src="https://github.com/cszn/cszn.github.io/blob/master/files/wm_fnb_0010_16.gif"/>
  </a>
</p>



Swin-Conv-UNet (SCUNet) denoising network
----------
<img src="figs/arch_scunet.png" width="900px"/> 


This is a Image denoising project which is constructed using SCU-NET architecture.
The "Swin-Conv-Unet" architecture is a combination of two popular deep learning architectures: the "Swin Transformer" and the "U-Net".
The architecture is used to train the model.

The *Swin Transformer* is a variant of the transformer architecture originally proposed for natural language processing tasks but adapted for computer vision tasks.
It replaces the traditional convolutional layers in CNNs with self-attention layers, allowing for global information exchange between image patches.

The *U-Net* architecture is commonly used for image segmentation tasks. It consists of an encoder network and a decoder network.
The encoder extracts high-level features from the input image, while the decoder reconstructs the segmentation map by upsampling and merging features from different resolutions.

Here we have used the pretrained data model which is tarined on above mentioned architecture to deploy this project.
The results accuracy is up to the mark and gives a fairly sharped and denoised version of the input image on processing it with our trained model.



Codes
---------
1. Download SCUNet models
```python
python main_download_pretrained_models.py --models "SCUNet" --model_dir "model_zoo"
```

2. Gaussian denoising
    1. grayscale images

    ```bash
    python main_test_scunet_gray_gaussian.py --model_name scunet_gray_25 --noise_level_img 25 --testset_name set12
    ```

    2. color images
    ```bash
    python main_test_scunet_color_gaussian.py --model_name scunet_color_25 --noise_level_img 25 --testset_name bsd68
    ```
3. Blind real image denoising

    ```bash
    python main_test_scunet_real_application.py --model_name scunet_color_real_psnr --testset_name real3
    ```




