# TWiLight Menu++ CJK 字形位图工具

[English](README.md)

用于把 CJK 字体渲染为像素对齐 BMP 字形图的 Python 工具。生成的 BMP 可通过兼容的 NFTR 编辑器导入 TWiLight Menu++ 字体。

这些脚本只生成供导入使用的位图，不会直接创建或修改 NFTR 文件。

![TWiLight Menu++ 字体效果对比](comparison.jpg)

> [!IMPORTANT]
> Python 脚本由 Gemini 协助开发。导入字体前请按原始像素尺寸检查生成结果。

## 所需环境

- Python 3 和 Pillow；
- `sd:/_nds/TWiLightMenu/extras/fonts/Default/` 中的 `small.nftr` 或 `large.nftr`；
- 从 NFTR 编辑器导出的 JSON 字符顺序表；
- 支持从位图导入 tiles 的 NFTR 编辑器。

安装 Pillow：

```powershell
python -m pip install Pillow
```

## 脚本说明

| 脚本 | 用途 |
| --- | --- |
| `PixelBitmap_Base.py` | 使用固定偏移生成单字体 BMP 字形图 |
| `PixelBitmap_AutoCenter.py` | 自动将非 CJK 字符在单元格中水平居中 |
| `PixelBitmap_DualFallback.py` | 主字体缺字时使用副字体，并允许分别调整偏移 |
| `PixelBitmap_ColorFix.py` | 统一位图颜色，修复导入前的抗锯齿或偏色问题 |

脚本会显示文件选择窗口，用于选择字符表 JSON、字体、可选副字体和输出 BMP。

## 制作流程

1. 从目标 NFTR 导出字符顺序 JSON。
2. 根据对齐和补字需求运行对应脚本。
3. 以原始分辨率检查生成的 BMP。
4. 使用 NFTR 编辑器把 BMP tiles 导入原始 NFTR。
5. 将保存后的字体放入 `sd:/_nds/TWiLightMenu/extras/fonts/<字体名>/`，并在实机上测试。

脚本默认使用 `12 × 16` 的小字体单元格或 `14 × 17` 的大字体单元格。批量生成前应先确认单元格、字号和偏移参数。

## 字体与 Release

仓库包含由文泉驿点阵宋体和 Fusion Pixel Font 衍生的 BDF 文件，原字体许可证继续适用。现有 Release 提供纯文泉驿及文泉驿/Fusion 组合版本。
