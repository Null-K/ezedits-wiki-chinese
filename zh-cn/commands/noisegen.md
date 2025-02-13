# 噪声生成

所有子命令都在`//eznoisegen` (`//noisegen`, `//ng`) 下 \
例如 `//ng heightmap`

## `//eznoisegen ...`

### heightmap

<details>

<summary>高度图</summary>

**`//eznoisegen heightmap <palette> <noise> [height] [-z <zoom>] [-s <seed>] [-o <offset>] [-ct]`**

* **Palette**: 指定要使用的方块调色板。
* **Noise**: 定义要使用的噪声预设。
* **Height** (默认值: 0): 控制从选择区域底部开始的高度。值为0将采用选择区域的高度。
  _如果高度足够大，可以将方块放置在选择区域上方_
* **-z** (默认值: 1): 调整噪声的缩放级别。
* **-s** (默认值: -1): 设置噪声种子。
* **-o** (默认值: (0,0,0)): 按给定的向量（X,Y,Z）偏移噪声生成坐标。
* **-c**: 使用时，将噪声生成居中于选择区域的世界坐标。
* **-t**: 启用平滑模式，专为调色板中的雪、水和熔岩方块设计 [仅在高度图模式下适用]。

</details>

### terrain

<details>

<summary>地形（3D）</summary>

**`//eznoisegen terrain <palette> <noise> [height] [strength] [-z <scale>] [-s <seed>] [-l <smear>] [-o <offset>] [-chnt]`**

* **Palette**: 指定要使用的方块调色板。
* **Noise**: 定义要使用的噪声预设。
* **Height** (默认值: 0): 控制从选择区域底部开始的高度。值为0将采用选择区域的高度。
  _如果高度足够大，可以将方块放置在选择区域上方_
* **Strength** (默认值: 1,0.5,0): 接受最多3个用逗号分隔的值，这些值控制各高度处的噪声强度：
  - *`0.5`表示各处强度均为50%*
  - *`0.7,0`表示最底部的强度为70%，顶部为0%，中间为平滑过渡*
  - *`0,1,0`表示底部强度为0%，中间为100%，顶部为0%*
* **-z** (默认值: 1): 调整噪声的缩放级别。
* **-s** (默认值: -1): 设置噪声种子。
* **-l** (默认值: 0): 应用垂直涂抹到3D噪声。
* **-o** (默认值: (0,0,0)): 按给定的向量（X,Y,Z）偏移噪声生成坐标。
* **-c**: 使用时，将噪声生成居中于选择区域的世界坐标。

</details>

### advanced

<details>

<summary>高级噪声源</summary>

**`//eznoisegen <palette> <noise> [lowerThreshold] [upperThreshold] [-z <scale>] [-s <seed>] [-l <smear>] [-o <offset>] [-chnt]`**

* **Palette**: 指定要使用的方块调色板。
* **Noise**: 定义要使用的噪声预设。
* **Lower Threshold** (默认值: 0): 设置噪声生成的下阈值，支持WorldEdit表达式（范围：0-1.0）。
* **Upper Threshold** (默认值: 0.5): 设置噪声生成的上阈值，支持WorldEdit表达式（范围：0-1.0）。
* **-z** (默认值: 1): 调整噪声的缩放级别。
* **-s** (默认值: -1): 设置噪声种子。
* **-l** (默认值: 0): 应用垂直涂抹到3D噪声。
* **-o** (默认值: (0,0,0)): 按给定的向量（X,Y,Z）偏移噪声生成坐标。
* **-c**: 使用时，将噪声生成居中于选择区域的世界坐标。
* **-h**: 使用2D噪声激活高度图模式。\
  _高度图模式仅兼容长方体、圆柱体或多边形区域类型。_
* **-n**: 使用归一化（-1到1）选择居中坐标进行噪声生成。
* **-t**: 启用平滑模式，专为调色板中的雪、水和熔岩方块设计 [仅在高度图模式下适用]。

</details>
