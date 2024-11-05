<h2 align="center">  3D Shoes Customization : Style Transfer & 3D Reconstruction </h2>  
<h3 align="center"> [빅데이터분석학회] D&A Conference </h3>  
<h4 align="center"> (2023.08. ~ 2023.11.) </h4>  


![Aqua Lines](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/aqua.png)  

<br>

## 1. 배경 및 목적

- 3D 커스터마이징을 통해 개인 맞춤형 신발 제작
- 다양한 커스텀 이미지 지원, 그래픽 디자인 제작 등 사람의 기술력/노동의 양은 줄이고, 질을 높여주는 기대 효과 

<br/>

## 2. 주최 기관

- 주최/주관: AI빅데이터융합경영학과 빅데이터분석 학회 D&A

<br/>

## 3. 프로젝트 기간 
- 2023.07 ~ 2023.11 (5개월)

<br/>

## 4. 프로젝트 설명   
![Untitled](https://github.com/Ji-eun-Kim/Ji-eun-Kim/assets/124686375/69035244-20bf-4180-8493-3300b3afdcbc)

커스텀 하고 싶은 신발과 적용하고 싶은 스타일로 사용자가 원하는 부분의 커스텀 신발을 제작해주는 딥러닝 프로젝트를 진행하였다. 이를 통해 다양한 커스텀 이미지를 지원, 그래픽 디자인 등 사람의 기술력이 투입되지 않는 **3D 커스터마이징 서비스를 통한 개인 맞춤형 신발**을 만들 수 있을 것이라 기대된다.


Task는 총 3가지로, 1. **[Segment Anything Model]**(Segmentation), 2. **[CAP-VSTNet]**(Style Transfer), 3. **[One-2-3-45/Dream Gaussian]**(3D Reconstruction)로 진행하였고, **Gradio tool**을 사용하여 해당 컨퍼런스 발표 시 **배포**도 진행하였다. 

1. **Segment Anything Model(SAM)**    
신발 커스텀을 위해 2D 신발 이미지 Segmentation을 진행하였다. 모델의 경우, **Segment Anything Model(SAM)** 을 본 프로젝트에 사용하였다. 수집된 신발 종류에 대한 Segment 진행 후, Mask를 생성하였다. SAM(Segment Anything Model)의 경우, 사용자가 Bbox를 지정하는 방식과 Automatic한 방식이 존재했으며, **자동화 및 편리성**, 그리고 보다 **좋은 성능**을 위해 **Automatic** 방식으로 선정하였다. Automatic으로 생성된 Mask들을 부위에 맞게 다시 **Composition**하였고, 다음과 같은 Mask 결과물을 Image 합성에 활용하였다.

<img width="1000" alt="1" src="https://github.com/Ji-eun-Kim/Ji-eun-Kim/assets/124686375/dc756d91-fdb2-4400-bad1-eb05fc22ac16">


2. **CAP-VSTNet(Style Transfer)**      
신발 커스텀을 위해 **CAP-VSTNet: Content Affinity Preserved Versatile Style Transfer (CVPR 2023)** 을 사용하였다. Original Image(커스텀하고자 하는 신발)와 Style Image(적용하고자 하는 스타일)을 input으로 넣어, transfer을 진행하였다. 이후, **OpenCV 라이브러리**를 통해 **원본 이미지, 커스텀된 이미지, 그리고 Mask된 이미지와 결합**을 진행하여, 커스텀된 2D 신발을 제작하였다.  

![Untitiled3](https://github.com/Ji-eun-Kim/Ji-eun-Kim/assets/124686375/a40f8d5c-acf1-4c36-bc9d-707c52a2a329)  



3. **Dream Gaussian(3D Reconstruction)**  
이후, style이 새로 적용된 image로 3D Reconstruction을 진행하였다. 이 때 사용한 모델은 **DreamGaussian: Generative Gaussian Splatting for Efficient 3D Content Creation**을 사용하였다. 단 하나의 image를 input으로 넣게 되면 2D -> 3D로 output이 나오게 된다. 더 나은 성능 향상을 위해 **One-2-3-45** 을 추가로 사용하였다. 해당 모델은 input으로 들어온 image에 대한 객체의 각도를 인식해주는 모델이며, 해당 모델을 통해 Dream Gaussian에 image와 각도(option)으로 넣어 성능을 향상시켰다. 


<br>


<br>
<div align="left">

## 5. Demo Gif & Transferred Images 

<br>

<p float="center">
  <div align="center">
  <img src="video.gif" alt="Animated gif pacman game" height="350px" width="600px" />
</p>

</div>


<br>
<div align="center">

<img width="500" alt="3" src="https://github.com/Ji-eun-Kim/Ji-eun-Kim/assets/124686375/c03bea66-d158-4f4c-ba9b-a572e2ddfff8"> | <img width="500" alt="4" src="https://github.com/Ji-eun-Kim/Ji-eun-Kim/assets/124686375/cfac5e5f-73ae-4764-8986-e805b5f1f662">
---|---|      

<br/>

## 6. 팀원 및 담당 역할  
<div align="left">
<팀원>  
  
- 전공생 5명
  
<br>

<담당 역할>  
  
- SAM(Segment Anything Model) 실험 및 mask 생성
- one-2345 실험
- dreamgaussian 실험
- Code 통합

<br>

## 7. 발표 자료 및 Reference  

- 발표 자료   
https://drive.google.com/file/d/1Jt1fnHNPGgiIQA1vgt_MnyuqAvgECDib/view?usp=sharing


<br>



[Segment anything](https://github.com/facebookresearch/segment-anything)  
```
@article{kirillov2023segany,
  title={Segment Anything},
  author={Kirillov, Alexander and Mintun, Eric and Ravi, Nikhila and Mao, Hanzi and Rolland, Chloe and Gustafson, Laura and Xiao, Tete and Whitehead, Spencer and Berg, Alexander C. and Lo, Wan-Yen and Doll{\'a}r, Piotr and Girshick, Ross},
  journal={arXiv:2304.02643},
  year={2023}
}
```

[CAP-VSTNet](https://github.com/linfengWen98/CAP-VSTNet)
```
@inproceedings{wen2023cap,
  title={CAP-VSTNet: Content Affinity Preserved Versatile Style Transfer},
  author={Wen, Linfeng and Gao, Chengying and Zou, Changqing},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={18300--18309},
  year={2023}
}
```

[One-2-3-45](https://github.com/One-2-3-45/One-2-3-45)
```
@article{liu2023one2345,
  title={One-2-3-45: Any single image to 3d mesh in 45 seconds without per-shape optimization},
  author={Liu, Minghua and Xu, Chao and Jin, Haian and Chen, Linghao and Xu, Zexiang and Su, Hao and others},
  journal={arXiv preprint arXiv:2306.16928},
  year={2023}
}
```

[DreamGaussian](https://github.com/dreamgaussian/dreamgaussian)
```
@article{tang2023dreamgaussian,
  title={DreamGaussian: Generative Gaussian Splatting for Efficient 3D Content Creation},
  author={Tang, Jiaxiang and Ren, Jiawei and Zhou, Hang and Liu, Ziwei and Zeng, Gang},
  journal={arXiv preprint arXiv:2309.16653},
  year={2023}
}
```
<br>
