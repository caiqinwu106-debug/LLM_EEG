# LLM_EEG
数据集。
脑电图数据可在 https://github.com/perceivelab/eeg_visual_classification 下载。

相应的图片可在 https://image-net.org/

把这些文件放进文件夹Data/EEGDataset
从预训练模型中提取特征。
通过输入图像的描述，可以从 Llama-2 7b 中提取语义特征。Data/EmbeddingFiles/image_des.txt

通过将图像输入模型，可以从VGG-19中提取视觉特征。

训练语义编码器。
通过裁剪损失训练语义编码器，并微调分类。对应的权重在文件夹和文件夹中。python training/EEG_sem_clip.pypython training/EEG_sem_classification.pyWeights/EEG_Sem_EmbWeights/EEG_classification

训练视觉编码器。
通过剪辑损失训练视觉编码器。对应的权重在文件夹中。python training/EEG_vis_clip.pyWeights/EEG_Vis_Emb

通过滑动生成图像。
训练一个mlp模型，将语义嵌入映射到滑行嵌入空间，生成图像。python training/EEG2Glide.pypython training/generator.py

你可以直接生成使用我们论文中使用权重的图像：

python training/pretrained_generator.py --subject 1
评估结果。
计算指标。python evaluation/ClipScore.pypython evaluation/InceptionScore.pypython evaluation/SSIM.py

