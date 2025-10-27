# 安装
 python -m pip install paddlepaddle-gpu==3.2.0 -i https://www.paddlepaddle.org.cn/packages/stable/cu118/
 
 python -m pip install "paddleocr[all]"

## 使用
paddleocr ocr -i output\uploads\26d64477-864f-418b-8e32-136ddb711a46.jpg  --use_doc_orientation_classify False --use_doc_unwarping False --use_textline_orientation False
# 参数
这三个参数是 **PaddleOCR** 的运行选项，用于控制文档图像的预处理行为。它们分别对应 **文档方向分类**、**文档透视矫正**、**文本行方向检测** 等功能。下面是详细解释👇

---

### 🔹 `--use_doc_orientation_classify`

**作用：** 是否启用 **文档方向分类（doc orientation classify）**。

**功能说明：**

- PaddleOCR 会自动判断整张文档的旋转角度（如 0°、90°、180°、270°）。
    
- 当你扫描的文档倒置、侧放或旋转时，这个模块会自动识别方向并纠正。
    
- 适用于扫描件、照片拍摄的文档。
    

**默认值：** `True`  
**设置为 `False` 时：**

> 不再自动检测整页旋转方向，OCR 将直接按原图方向识别。  
> **适合场景：**  
> 图像已经是正的、批量处理速度要求高时，可关闭节省时间。

---

### 🔹 `--use_doc_unwarping`

**作用：** 是否启用 **文档矫正（unwarping）**。

**功能说明：**

- 当图像是纸张弯曲或拍摄有透视畸变时，该功能会做“展平矫正”。
    
- PaddleOCR 内部调用文档几何模型来将弯曲页面拉直，使文本更易于识别。
    
- 这一步是比较耗时的预处理操作。
    

**默认值：** `True`  
**设置为 `False` 时：**

> 不进行几何校正，直接识别原图。  
> **适合场景：**  
> 输入是扫描件或拍摄平整页面的图片，无需透视修正时关闭，可提升速度。

---

### 🔹 `--use_textline_orientation`

**作用：** 是否启用 **文本行方向检测（textline orientation）**。

**功能说明：**

- 针对某些复杂文档（如横排、竖排混排、表格、票据），自动检测每一行文本的方向。
    
- 在检测文字框后，会判断每个文字行是否倒置、竖排等，从而旋转单行进行识别。
    
- 典型场景：竖排中文、旋转文字、票据等。
    

**默认值：** `True`  
**设置为 `False` 时：**

> PaddleOCR 不再对每个文字行单独做方向判断，而是统一使用整图方向。  
> **适合场景：**  
> 所有文字方向一致（如横排文档）时，可关闭加速识别。

---

### ✅ 总结对比表

|参数|功能|默认|关闭后效果|适合关闭的场景|
|---|---|---|---|---|
|`--use_doc_orientation_classify`|自动判断整页方向|True|不自动旋转整页|图像方向固定|
|`--use_doc_unwarping`|矫正文档透视或弯曲|True|不做几何校正|扫描件或平整文档|
|`--use_textline_orientation`|检测每行文字方向|True|不做行级旋转|全部横排或竖排一致|

---

### 💡 实用建议

如果你在处理的是：

- **拍摄的纸质文档** → 建议都开 (`True`)
    
- **OCR批量处理扫描件** → 可以都关，加速推理
    
- **票据或竖排文字** → 保留 `use_textline_orientation=True`
    
- **部署在CPU、追求速度** → 全关 `False`，性能提升显著（约20~30%）
    
非常好的问题 ✅  
你提到的这四个模块（PP-OCRv5 的两个组件 + PP-StructureV3）虽然都属于 **PaddleOCR 系列模型家族**，但它们的**用途、输入输出、调用方式和应用场景**是不同层级的。下面我帮你系统地梳理对比 👇

---

## 🧩 一、总体关系图

```
         ┌─────────────────────────────┐
         │        PP-OCRv5（整套）     │
         │  ┌───────────────────────┐ │
         │  │ Text Detection 模块   │ │ → 负责“找文字在哪”
         │  └───────────────────────┘ │
         │  ┌───────────────────────┐ │
         │  │ Text Recognition 模块 │ │ → 负责“识别出文字内容”
         │  └───────────────────────┘ │
         └─────────────────────────────┘
                        │
                        ▼
           ┌────────────────────────┐
           │ PP-StructureV3          │ → 结构化理解文档（如表格、版面、字段）
           │ （在OCR结果上再理解）   │
           └────────────────────────┘
```

---

## 🧠 二、各模块用途与区别详解

|模块|主要作用|输入|输出|是否依赖其他模块|典型场景|
|---|---|---|---|---|---|
|**PP-OCRv5**|PaddleOCR 的整体版本（检测+识别）|图片|文本行+文字结果|自动调用检测+识别|通用OCR（扫描件、票据、证照）|
|**PP-OCRv5 Text Detection Module**|文本检测模块（检测文字区域）|图片|文本框坐标（bounding boxes）|✅ 通常与识别模块搭配使用|文本定位、版面检测|
|**PP-OCRv5 Text Recognition Module**|文本识别模块（识别具体文字内容）|单个文本块图像|文字字符串|❌ 可单独用|二次识别、微调任务|
|**PP-StructureV3**|文档结构化理解模型（在OCR基础上提取结构）|图片或OCR结果|文档结构（标题、表格、段落、key-value等）|✅ 依赖OCR结果|表格提取、发票/表单解析、文档重建|

---

## 🔍 三、使用方式区别

### 1️⃣ **PP-OCRv5（整套OCR）**

👉 一键完成“检测+识别”，最常用。

**命令行示例：**

```bash
paddleocr --image_dir ./test.jpg --use_angle_cls True --ocr_version PP-OCRv5
```

**返回结果：**

```python
[
  [[[x1, y1], [x2, y2], [x3, y3], [x4, y4]], ("识别文字", 0.98)],
  ...
]
```

> 用于普通OCR任务（身份证、合同、发票、表格截图等）。

---

### 2️⃣ **PP-OCRv5 Text Detection Module**

👉 单独用于“找文字区域”，不识别文字内容。

**示例代码：**

```python
from paddleocr import PaddleOCR

ocr = PaddleOCR(det_model_dir='path/to/det_model', use_angle_cls=False, rec=False)
result = ocr.ocr('test.jpg', det=True, rec=False)
```

**输出：**

```python
[[[x1, y1], [x2, y2], [x3, y3], [x4, y4]], ...]  # 文字框坐标
```

> 用于前处理任务：只想知道文字区域，比如遮挡敏感信息、版面分析。

---

### 3️⃣ **PP-OCRv5 Text Recognition Module**

👉 单独用于“识别文字”，输入是一个个小块图像。

**示例代码：**

```python
from paddleocr import PaddleOCR

ocr = PaddleOCR(det=False, rec_model_dir='path/to/rec_model')
result = ocr.ocr('crop_text_image.jpg', det=False, rec=True)
```

**输出：**

```python
[('识别文字', 0.99)]
```

> 用于二次识别、裁剪后的小图识别、模型微调测试。

---

### 4️⃣ **PP-StructureV3**

👉 在OCR基础上进一步理解文档结构，支持表格、版面、key-value抽取。

**示例命令：**

```bash
paddlestructure --image_dir ./invoice.jpg --ocr_version PP-OCRv5 --structure_version PP-StructureV3
```

**示例输出：**

```json
{
  "layout": [
    {"type": "title", "text": "发票"},
    {"type": "table", "cells": [...]},
    {"type": "key_value", "key": "金额", "value": "1000.00"}
  ]
}
```

> 适用于：
> 
> - 表格结构化提取（如Excel导出）
>     
> - 发票/合同字段识别
>     
> - 文档重建（如版面识别、段落重排）
>     

---

## 🧩 四、功能层级对比总结表

|模块|属于|功能层级|是否识别文字|是否结构化输出|应用场景|
|---|---|---|---|---|---|
|PP-OCRv5|整体OCR系统|综合（检测+识别）|✅|❌|通用OCR|
|PP-OCRv5 Text Detection|子模块|检测|❌|❌|只检测文字区域|
|PP-OCRv5 Text Recognition|子模块|识别|✅|❌|对局部区域识别|
|PP-StructureV3|上层系统|文档理解|✅（依赖OCR）|✅|表格/合同/报告解析|

---

## 💡 实际使用建议

|目标任务|推荐模型组合|
|---|---|
|普通OCR（识别文字内容）|**PP-OCRv5（整套）**|
|只想检测文字区域|**PP-OCRv5 Detection Module**|
|已有文字块图像，只想识别文字|**PP-OCRv5 Recognition Module**|
|结构化提取表格、发票、报告字段|**PP-StructureV3 + PP-OCRv5**|

---

是否希望我帮你画一张这四个模块的关系与调用流程图（检测→识别→结构化）？那样能更直观地理解整个 pipeline。