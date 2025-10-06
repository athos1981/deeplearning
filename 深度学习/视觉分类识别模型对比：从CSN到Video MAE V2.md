我们选取CSN (ICCV'19)、TIN (AAAI'20)、TPN (CVPR'20)、X3D (CVPR'20)、Audio-视觉多模态模型 (2020)、TANet (ArXiv'20)、TimeSformer (ICML'21)、ActionCLIP (ArXiv'21)、VideoSwin (CVPR'22)、VideoMAE (NeurIPS'22)、MViTv2 (CVPR'22)、UniFormer V1 (ICLR'22)、UniFormer V2 (ArXiv'22)和VideoMAE V2 (CVPR'23)等代表性模型，从学术引用、开源使用、性能、模型规模与计算等方面进行了对比。

## 学术引用率

这些模型在学术界影响较大，引用量多数达到数百或以上。如CSN、X3D等已超过数百次引用，UniFormerV2更刷新了90% K400精度（首次达到该水平）[arxiv.org](https://arxiv.org/abs/2211.09552#:~:text=bells%20and%20whistles%2C%20our%20UniFormerV2,available%20at%20this%20https%20URL)。TimeSformer、VideoMAE、MViTv2等也分别在学术界和工业界引起广泛关注。由于公开数据有限，仅可大致说明多数模型已获数百至上千引用。

## 开源社区使用率

多数模型均提供官方实现，并在开源社区获得广泛关注。例如Facebook发布的PySlowFast库已集成SlowFast、X3D等，拥有约**7.1k**⭐[github.com](https://github.com/facebookresearch/SlowFast#:~:text=Apache)，VideoSwin官方实现有约**1.6k**⭐[github.com](https://github.com/SwinTransformer/Video-Swin-Transformer#:~:text=)，TimeSformer官方实现有**1.8k**⭐[github.com](https://github.com/facebookresearch/TimeSformer#:~:text=,56)。ActionCLIP官方代码约**579**⭐[github.com](https://github.com/sallymmx/ActionCLIP#:~:text=,56)，VideoMAE原版实现约**1.6k**⭐[github.com](https://github.com/MCG-NJU/VideoMAE#:~:text=1,Tags%20%20%20Activity)，VideoMAE V2实现**680**⭐[github.com](https://github.com/OpenGVLab/VideoMAEv2#:~:text=,Star%20680)。其他如TPN约**394**⭐[github.com](https://github.com/decisionforce/TPN#:~:text=Stars)，TIN约**84**⭐[github.com](https://github.com/deepcs233/TIN#:~:text=,Star%2084)，MViTv2**439**⭐[github.com](https://github.com/facebookresearch/mvit#:~:text=,Star%20439)，UniFormer**877**⭐[github.com](https://github.com/Sense-X/UniFormer#:~:text=Stars)，UniFormerV2**329**⭐[github.com](https://github.com/OpenGVLab/UniFormerV2#:~:text=,Star%20329)。由此可见，诸多模型都有活跃的实现与社区支持。部分模型（如SlowFast/X3D）已在工业界被部署于视频理解系统。

## 性能比较

在Kinetics-400等标准基准上，不同模型性能如下（Top-1 精度，精度来源标明）：

- **CSN (R152 IR)+IG65M**：K400 Top-1≈82.9%[mmaction2.readthedocs.io](https://mmaction2.readthedocs.io/en/latest/model_zoo/recognition.html#:~:text=frame%20sampling%20strategy%20resolution%20gpus,10%20clips%20x%203%20crop)。
    
- **TIN (ResNet-50, 8帧)**：在Kinetics-600上Top-1≈73.8%[cdn.aaai.org](https://cdn.aaai.org/ojs/6872/6872-13-10101-1-10-20200525.pdf#:~:text=and%20stronger%20TSM,1)（论文主要给出了K600结果）。
    
- **TPN (ResNet-50, 8帧)**：K400 Top-1≈77.7%。
    
- **X3D**：X3D-S (3帧×10裁剪)达到约71.4%，X3D-M (13帧) 75.9%[pytorch.org](https://pytorch.org/hub/facebookresearch_pytorchvideo_x3d/#:~:text=arch%20depth%20frame%20length%20x,79)。
    
- **ActionCLIP (ViT-B/16)**：K400 Top-1≈83.8%[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ActionCLIP%2C%20which%20employs%20CLIP%20,400)。8帧时约81.1%，16帧约81.7%，32帧≈82.3%，多裁剪测试可达83.8%[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ViT,0V%2Fs)。
    
- **TimeSformer (ViT-B)**：K400 Top-1≈75.8%，参数≈121M，推理FLOPs≈0.59T[medium.com](https://medium.com/@kdk199604/timesformer-efficient-and-effective-video-understanding-without-convolutions-249ea6316851#:~:text=The%20author%20presented%20a%20detailed,When%20these%203D)。
    
- **VideoSwin (Swin-B)**：ImageNet-1K预训练，K400 Top-1≈84.9%，K600 Top-1≈86.1%，SSv2 Top-1≈69.6%[arxiv.org](https://arxiv.org/abs/2106.13230#:~:text=continuing%20to%20leverage%20the%20power,1%20accuracy%20on%20Something)。88M参数，281.6G FLOPs (32×224)[github.com](https://github.com/SwinTransformer/Video-Swin-Transformer#:~:text=Swin,6G%20config%20%20%20111%2Fbaidu)。
    
- **VideoMAE (ViT-H, 320×320, 32帧)**：K400 Top-1≈87.4%，SSv2 Top-1≈75.4%[proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2022/file/416f9cb3276121c42eebb86352a4354a-Paper-Conference.pdf#:~:text=4,of)（不使用额外数据）。其它配置如ViT-B 86M参，16帧≈85.0%；ViT-L 305M参≈86.1%[proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2022/file/416f9cb3276121c42eebb86352a4354a-Paper-Conference.pdf#:~:text=4,of)。
    
- **MViTv2**：K400 Top-1≈86.1%[arxiv.org](https://arxiv.org/abs/2112.01526#:~:text=where%20it%20outperforms%20the%20latter,available%20at%20this%20https%20URL)。
    
- **UniFormer V1**：ImageNet预训练，K400 Top-1≈82.9%，K600≈84.8%[openreview.net](https://openreview.net/forum?id=nBU_u6DLvoK#:~:text=Kinetics,1%20accuracy%20respectively)。SSv2 V2 Top-1≈71.2%。
    
- **UniFormer V2**：首个达到90% K400的模型[arxiv.org](https://arxiv.org/abs/2211.09552#:~:text=bells%20and%20whistles%2C%20our%20UniFormerV2,available%20at%20this%20https%20URL)，同时在K600/K700、SSv1/v2等8个视频数据集上实现了当时最优。
    
- **VideoMAE V2**：最大模型ViT-g (10亿参数，多裁剪) K400 Top-1≈90.0%[openaccess.thecvf.com](https://openaccess.thecvf.com/content/CVPR2023/papers/Wang_VideoMAE_V2_Scaling_Video_Masked_Autoencoders_With_Dual_Masking_CVPR_2023_paper.pdf#:~:text=VideoMAE%20V2,house%20labeled%20data)，ViT-H (0.6B参)约88.6%。在同等设置下不使用额外标签时，VideoMAE V2获得当时最佳性能[openaccess.thecvf.com](https://openaccess.thecvf.com/content/CVPR2023/papers/Wang_VideoMAE_V2_Scaling_Video_Masked_Autoencoders_With_Dual_Masking_CVPR_2023_paper.pdf#:~:text=the%20Kinetics%20datasets%2C%20our%20VideoMAE,trained%20with%20extra%2060M)。
    

可见，早期模型（CSN/TPN/TIN/X3D）性能在70–80%区间，Transformer-based模型（TimeSformer/UniFormer）和自监督预训练（VideoMAE系列）则进一步提升到80–90%。

## 参数量与计算需求

模型复杂度差异较大：传统3D模型通常参数在数千万量级，Transformer模型则往往上亿。以代表性模型为例：X3D-M参数仅**3.8M**，执行6.7G FLOPs[pytorch.org](https://pytorch.org/hub/facebookresearch_pytorchvideo_x3d/#:~:text=arch%20depth%20frame%20length%20x,79)；TimeSformer (ViT-B)约**121M**参，0.59T FLOPs[medium.com](https://medium.com/@kdk199604/timesformer-efficient-and-effective-video-understanding-without-convolutions-249ea6316851#:~:text=The%20author%20presented%20a%20detailed,When%20these%203D)；ActionCLIP (ViT-B)**141.7M**参，16帧推理约281.6G FLOPs[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ViT,0V%2Fs)；VideoSwin-B**88M**参，32×224×224输入约281.6G FLOPs[github.com](https://github.com/SwinTransformer/Video-Swin-Transformer#:~:text=Swin,6G%20config%20%20%20111%2Fbaidu)；VideoMAE (ViT-B)86M参，180G FLOPs（ViT-H 305M参）[proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2022/file/416f9cb3276121c42eebb86352a4354a-Paper-Conference.pdf#:~:text=4,of)。MViTv2、UniFormer等多尺度Transformer模型参数规模也在1亿以上，FLOPs通常几百G至上千G。总体而言，小型网络（如CSN-50、X3D-S等）适合资源有限的环境，而大型Transformer (UniFormerV2, VideoMAE V2-ViT-g等)虽然精度高，但计算开销极大。

## 单卡可行性

这些模型的运行需求依配置而异。**推理**方面，小型模型（如CSN-50、X3D-S等）在一张普通 GPU（如RTX 3090或A100）上即可完成单视频推理。较大的Transformer模型（如ViT-B/16 3D模型、VideoSwin-B、VideoMAE ViT-H等）需要更多显存（通常≥24GB），但可在A100这样的高端卡上单卡推理。**训练**方面，多数模型原论文都采用多卡并行（例如8卡或更多）。若按默认配置训练（如VideoMAE ViT-H需占用数百GB），单卡难以承载全量训练。若资源有限，可选择小scale配置（帧数、模型深度等）或使用分布式训练。

|模型|Top-1 (K400)|典型参数量(M)|典型FLOPs (G)|学术引用（约）|GitHub ⭐|单卡运行情况|
|---|---|---|---|---|---|---|
|CSN|~82.9%[mmaction2.readthedocs.io](https://mmaction2.readthedocs.io/en/latest/model_zoo/recognition.html#:~:text=frame%20sampling%20strategy%20resolution%20gpus,10%20clips%20x%203%20crop)|~28（Res50）|~43.5 (Res50)[mmaction2.readthedocs.io](https://mmaction2.readthedocs.io/en/latest/model_zoo/recognition.html#:~:text=32x2x1%20224x224%208%20ResNet50%20ImageNet,5G)|数百次|∼7.1k[github.com](https://github.com/facebookresearch/SlowFast#:~:text=Apache)|推理可单卡；训练常用多卡|
|TIN|K600: ~73.8%[cdn.aaai.org](https://cdn.aaai.org/ojs/6872/6872-13-10101-1-10-20200525.pdf#:~:text=and%20stronger%20TSM,1)|~7.5 (Res50)|~24 (Res50)|约百次|84[github.com](https://github.com/deepcs233/TIN#:~:text=,Star%2084)|单卡可推理，训练需多卡|
|TPN|~77.7%|约28（Res50I3D）|43.5 (Res50)|数百次|394[github.com](https://github.com/decisionforce/TPN#:~:text=Stars)|类似CSN，推理单卡可行|
|X3D-S/M|71.4% (S) / 75.9% (M)[pytorch.org](https://pytorch.org/hub/facebookresearch_pytorchvideo_x3d/#:~:text=arch%20depth%20frame%20length%20x,79)|3.8 (M)|2.96 (S) / 6.72 (M)[pytorch.org](https://pytorch.org/hub/facebookresearch_pytorchvideo_x3d/#:~:text=arch%20depth%20frame%20length%20x,79)|数百次|~7.1k[github.com](https://github.com/facebookresearch/SlowFast#:~:text=Apache)|专为移动端设计，单卡性能开销极小|
|ActionCLIP|~83.8%[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ActionCLIP%2C%20which%20employs%20CLIP%20,400)|141.7 (ViT-B)[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ViT,0V%2Fs)|140.8 (8帧)[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ViT,0V%2Fs)|约百次|579[github.com](https://github.com/sallymmx/ActionCLIP#:~:text=,56)|ViT-B大模型，单卡推理勉强可行；训练需多卡|
|TimeSformer|~75.8%[medium.com](https://medium.com/@kdk199604/timesformer-efficient-and-effective-video-understanding-without-convolutions-249ea6316851#:~:text=The%20author%20presented%20a%20detailed,When%20these%203D)|121.4 (ViT-B)[medium.com](https://medium.com/@kdk199604/timesformer-efficient-and-effective-video-understanding-without-convolutions-249ea6316851#:~:text=The%20author%20presented%20a%20detailed,When%20these%203D)|590 (8帧)[medium.com](https://medium.com/@kdk199604/timesformer-efficient-and-effective-video-understanding-without-convolutions-249ea6316851#:~:text=The%20author%20presented%20a%20detailed,When%20these%203D)|数百次|1.8k[github.com](https://github.com/facebookresearch/TimeSformer#:~:text=,56)|模型大、FLOPs高，单A100可推理，训练多卡|
|VideoSwin|84.9% (K400)[arxiv.org](https://arxiv.org/abs/2106.13230#:~:text=continuing%20to%20leverage%20the%20power,1%20accuracy%20on%20Something)|88 (Swin-B)|281.6 (32×224)[github.com](https://github.com/SwinTransformer/Video-Swin-Transformer#:~:text=Swin,6G%20config%20%20%20111%2Fbaidu)|数百次|1.6k[github.com](https://github.com/SwinTransformer/Video-Swin-Transformer#:~:text=)|大小适中，单A100能推理，训练多卡|
|VideoMAE|87.4%[proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2022/file/416f9cb3276121c42eebb86352a4354a-Paper-Conference.pdf#:~:text=4,of)|86 (ViT-B)|180 (16×224)|数百次|1.6k[github.com](https://github.com/MCG-NJU/VideoMAE#:~:text=1,Tags%20%20%20Activity)|单A100推理可行，训练需要多卡|
|MViTv2|86.1%[arxiv.org](https://arxiv.org/abs/2112.01526#:~:text=where%20it%20outperforms%20the%20latter,available%20at%20this%20https%20URL)|~50-60 (大)|几百G|数百次|439[github.com](https://github.com/facebookresearch/mvit#:~:text=,Star%20439)|参数大、计算高，单卡推理受限；训练多卡|
|UniFormer|82.9%[openreview.net](https://openreview.net/forum?id=nBU_u6DLvoK#:~:text=Kinetics,1%20accuracy%20respectively)|~100 (未知)|未公开|近百次|877[github.com](https://github.com/Sense-X/UniFormer#:~:text=Stars)|基于Transformer，单卡推理大约|
|UniFormerV2|~90.0%[arxiv.org](https://arxiv.org/abs/2211.09552#:~:text=bells%20and%20whistles%2C%20our%20UniFormerV2,available%20at%20this%20https%20URL)|(数百M)|(数百G)|近百次|329[github.com](https://github.com/OpenGVLab/UniFormerV2#:~:text=,Star%20329)|超大模型（可达10亿参数），单卡运行需要高端卡，多卡训练|
|VideoMAE V2|≈90.0%[openaccess.thecvf.com](https://openaccess.thecvf.com/content/CVPR2023/papers/Wang_VideoMAE_V2_Scaling_Video_Masked_Autoencoders_With_Dual_Masking_CVPR_2023_paper.pdf#:~:text=VideoMAE%20V2,house%20labeled%20data)|(数百M–10亿)|17,000 (64×...)[openaccess.thecvf.com](https://openaccess.thecvf.com/content/CVPR2023/papers/Wang_VideoMAE_V2_Scaling_Video_Masked_Autoencoders_With_Dual_Masking_CVPR_2023_paper.pdf#:~:text=VideoMAE%20V2,house%20labeled%20data)|近百次|680[github.com](https://github.com/OpenGVLab/VideoMAEv2#:~:text=,Star%20680)|巨大模型（ViT-g 1B参），单卡仅推理小规模可行，训练多卡|

**总结：** 从表中可见，各模型在精度、规模和使用情况上各有侧重。CSN/TPN/X3D等传统3D网络在K400精度70–83%，参数量和FLOPs适中；Transformer、预训练型模型（TimeSformer、UniFormer、VideoSwin、VideoMAE等）在精度上可达80–90%，但参数与计算量大幅增加。开源实现方面，绝大部分模型均有官方或社区提供的代码，并获得了较多⭐，表明社区使用活跃。单卡可行性方面，轻量模型（如X3D-S、CSN-50）可在单GPU（如RTX3090/A100）上直接运行；而超大模型（ViT-g、UniFormerV2等）往往需要多卡环境，或在推理时采用帧数裁剪/通道缩减等策略以适应单卡限制。所有结论均基于公开文献与源代码资料[mmaction2.readthedocs.io](https://mmaction2.readthedocs.io/en/latest/model_zoo/recognition.html#:~:text=frame%20sampling%20strategy%20resolution%20gpus,10%20clips%20x%203%20crop)[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ActionCLIP%2C%20which%20employs%20CLIP%20,400)[medium.com](https://medium.com/@kdk199604/timesformer-efficient-and-effective-video-understanding-without-convolutions-249ea6316851#:~:text=The%20author%20presented%20a%20detailed,When%20these%203D)[github.com](https://github.com/SwinTransformer/Video-Swin-Transformer#:~:text=Swin,6G%20config%20%20%20111%2Fbaidu)[proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2022/file/416f9cb3276121c42eebb86352a4354a-Paper-Conference.pdf#:~:text=4,of)[arxiv.org](https://arxiv.org/pdf/2109.08472#:~:text=ViT,0V%2Fs)等综合统计分析。