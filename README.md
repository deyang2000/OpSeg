# 🌓 OpSeg: Instance Shadow Segmentation with SAM2.1_b+

<div align="center">

📸 **Official Implementation of IJCNN 2025 Paper**
**“OpSeg: Adapting Segment Anything Model 2 with Prompts for Efficient Instance Shadow Detection”**

[![Paper](https://img.shields.io/badge/Paper-IJCNN%202025-blue)](https://ieeexplore.ieee.org/)
[![ModelScope](https://img.shields.io/badge/ModelScope-SAM2__Shadow-green)](https://modelscope.cn/models/deyang2000/SAM2_Shadow)
[![License](https://img.shields.io/badge/License-Apache%202.0-yellow)](LICENSE)

</div>

---

## 📘 简介 (Introduction)
<img width="1329" height="569" alt="image" src="https://github.com/user-attachments/assets/e92ebb7f-8da3-41e6-a683-4c3d75575352" />

本仓库提供了 **SAM2.1_b+ 模型** 在 **SOBA 实例阴影分割数据集** 上的微调版本。
该模型具备对**物体与其阴影进行联合实例分割**的能力，可作为通用视觉分割任务中对阴影敏感场景的增强版模型。

This repository provides a **fine-tuned version of SAM2.1_b+** on the **SOBA Instance-Shadow Segmentation Dataset**, enabling **joint segmentation of objects and their shadows**.
It serves as an enhanced foundation for general visual segmentation tasks where **shadow understanding** is important.

---

## 🧠 模型背景 (Background)

> **“OpSeg: Adapting Segment Anything Model 2 with Prompts for Efficient Instance Shadow Detection” (IJCNN 2025)**
> 该仓库为论文的官方实现。我们计划在更大规模、更丰富的阴影实例数据集上继续扩展并微调其他 SAM 版本。

> **“OpSeg: Adapting Segment Anything Model 2 with Prompts for Efficient Instance Shadow Detection” (IJCNN 2025)**
> This repository serves as the official implementation. We plan to extend to more diverse shadow datasets and other SAM variants.

---

## 🚀 性能与结果 (SOTA Performance)

据我们所知，在 **SOBA** 数据集的带 prompt 的测试集与挑战集上，**OpSeg** 取得了最优结果（参考自 [MetaShadow, CVPR 2025](https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_MetaShadow_Object-Centered_Shadow_Detection_Removal_and_Synthesis_CVPR_2025_paper.pdf)）。

|    Dataset    | Target | Metric |  Ori. |  Fz.  |               Ft.              | ↑Δ (%) |
| :-----------: | :----: | :----: | :---: | :---: | :----------------------------: | :----: |
|    **Test**   | Object |  mIoU  | 0.630 | 0.799 |            **0.877**           |  +39.2 |
|    **Test**   | Shadow |  mIoU  | 0.236 | 0.554 | **0.763** *(MetaShadow 0.710)* | +223.4 |
| **Challenge** | Object |  mIoU  | 0.633 | 0.732 |            **0.851**           |  +34.4 |
| **Challenge** | Shadow |  mIoU  | 0.165 | 0.433 |            **0.671**           | +307.4 |

<details>
<summary>Full Results (点击展开)</summary>

| Metric                  |  Ori. |  Fz.  | %Δ Fz ↑ |             Ft.            | %Δ Ft ↑ |
| :---------------------- | :---: | :---: | :-----: | :------------------------: | :-----: |
| **Test - Objects**      |       |       |         |                            |         |
| mIoU                    | 0.630 | 0.799 |   26.7  |            0.877           |   39.2  |
| mDice                   | 0.694 | 0.850 |   22.5  |            0.917           |   32.1  |
| W.IoU                   | 0.718 | 0.830 |   15.6  |            0.908           |   26.5  |
| W.Dice                  | 0.779 | 0.877 |   12.6  |            0.942           |   20.9  |
| **Test - Shadows**      |       |       |         |                            |         |
| mIoU                    | 0.236 | 0.554 |  134.6  | 0.763 *(MetaShadow 0.710)* |  223.4  |
| mDice                   | 0.295 | 0.658 |  123.0  |            0.842           |  185.4  |
| W.IoU                   | 0.167 | 0.546 |  226.8  |            0.781           |  367.4  |
| W.Dice                  | 0.218 | 0.642 |  194.7  |            0.847           |  289.2  |
| **Challenge - Objects** |       |       |         |                            |         |
| mIoU                    | 0.633 | 0.732 |   15.6  |            0.851           |   34.4  |
| mDice                   | 0.707 | 0.803 |   13.5  |            0.901           |   27.4  |
| W.IoU                   | 0.749 | 0.791 |   5.6   |            0.881           |   17.7  |
| W.Dice                  | 0.817 | 0.857 |   4.8   |            0.922           |   12.8  |
| **Challenge - Shadows** |       |       |         |                            |         |
| mIoU                    | 0.165 | 0.433 |  163.1  |            0.671           |  307.4  |
| mDice                   | 0.214 | 0.545 |  154.3  |            0.763           |  256.1  |
| W.IoU                   | 0.095 | 0.389 |  311.1  |            0.688           |  627.3  |
| W.Dice                  | 0.128 | 0.493 |  285.3  |            0.765           |  497.9  |

</details>



---

## 🛠 推荐工具 (Recommended Tool)

* **ISAT**（交互式半自动标注工具，整合 SAM 家族能力，包括视频追踪与多帧交互）：
  [https://github.com/yatengLG/ISAT_with_segment_anything.git](https://github.com/yatengLG/ISAT_with_segment_anything.git)

---

## 💾 模型下载 (Model Download)

**ModelScope**

```bash
pip install modelscope
```

```python
from modelscope import snapshot_download
model_dir = snapshot_download('deyang2000/SAM2_Shadow')
```

**Google Drive**
👉 [Download from Google Drive](https://drive.google.com/file/d/1K7HwdSrK9O9kfKF0F7X_7-T_6McGjG4j/view?usp=sharing)

在ISAT中使用该checkpoint时，你只需要将文件名修改为sam2.1_hiera_base_plus即可。
---

💡 **在 ISAT 中使用时：**
只需将下载得到的权重文件重命名为：

```bash
sam2.1_hiera_base_plus
```

然后放入 ISAT 工具的 `checkpoints/` 目录下即可自动识别。


## 📚 引用 (Citation)

```bibtex
@inproceedings{li2025opseg,
  title     = {OpSeg: Adapting Segment Anything Model 2 with Prompts for Efficient Instance Shadow Detection},
  author    = {Yanfei Li and Jun Xu and Yuan Zeng and Yi Gong},
  booktitle = {Proceedings of the 2025 IEEE International Joint Conference on Neural Networks (IJCNN)},
  year      = {2025},
  address   = {Rome, Italy},
  publisher = {IEEE},
  note      = {Official Implementation: https://www.modelscope.cn/deyang2000/SAM2_Shadow}
}
```

---

## 📄 License

Apache License 2.0. See [LICENSE](LICENSE).
