# 噪声详解

对于从未接触过噪声的人来说，这可能是一个复杂的话题，但最简单的说，噪声是一种通过某些输入（通常是 X、Y、Z 坐标）获取值的方法。

你最熟悉噪声的地方可能是 Minecraft 的地形生成。在世界的每一个点，多个噪声函数结合起来决定是否放置一个方块，如果是的话，还会决定放置哪个方块。

在 ezEdits 中，我们基本上就是这样做的，使用噪声生成形状、地形和纹理。



在这个插件中，你会发现几种不同类型的噪声，每种噪声都有不同的特性，尤其是 Cellular 噪声，它带有许多额外的可自定义参数。

一些使用噪声的功能包括：

* `//eznoisegen ...` - *噪声生成指令*
* `#eznoisemask` - *蒙版*
* `//ezbrush gradient ...` - *笔刷*



_ezEdits 中的噪声基于修改后的 FastNoiseLite 版本，因此我们强烈推荐使用这个网站来试验噪声参数：_ [_http://auburn.github.io/FastNoiseLite/_ ](http://auburn.github.io/FastNoiseLite/)

## 噪声参数

每个参数和许多值都有简写，例如 "Fractal" 代替 "FractalType" 或 "Simplex" 代替 "OpenSimplex2"。在可能的地方，简写将显示在括号中。\
<mark style="color:red;">`红色 = 参数`</mark>    <mark style="color:purple;">`紫色 = 值`</mark>

&#x20;

### 噪声类型

<details>

<summary>设置噪声类型<br><mark style="color:red;"></summary>

Sets the type of noise to be used. This is the start of any noise and will be in the format of `Noise()`, for example `Perlin()`, where all other parameters will go between the brackets.

* <mark style="color:purple;">`Perlin (per)`</mark>
* <mark style="color:purple;">`OpenSimplex2 (simplex)`</mark>
* <mark style="color:purple;">`OpenSimplex2S (smooth)`</mark>
* <mark style="color:purple;">`Value (val)`</mark>
* <mark style="color:purple;">`ValueCubic (cubic)`</mark>
* <mark style="color:purple;">`White`</mark>
* <mark style="color:purple;">`Cellular (vor)`</mark>
* <mark style="color:purple;">`Shard`</mark>

</details>

### Basic Noise Parameters

<details>

<summary>Basic Noise Parameters</summary>

* <mark style="color:red;">`Seed`</mark>\
  Sets the seed value for the noise. -1 or no value will result in a random noise seed.
* <mark style="color:red;">`Frequency (Freq)`</mark>\
  Sets the frequency for the noise. A higher frequency will lead to steeper noise, a lower value will lead to smoother noise.
* <mark style="color:red;">`Inverted (Invert)`</mark>\
  Whether to invert the noise value or not. Default is false.
  * <mark style="color:purple;">`True`</mark>
  * <mark style="color:purple;">`False`</mark>
* <mark style="color:red;">`ValueMapping (Map)`</mark>\
  Whether to ignore or override the value mapping. By default noise is sampled to map between 0 and 1.
  * <mark style="color:purple;">`Default (Def)`</mark>
  * <mark style="color:purple;">`None (No)`</mark>
  * <mark style="color:purple;">`Override (OR)`</mark>\
    **If Overridden:**
    * <mark style="color:red;">`LowerBound (Min)`</mark>
    * <mark style="color:red;">`UpperBound (Max)`</mark>
* <mark style="color:red;">`YScaling (Y)`</mark>\
  When using 3D noises this can be used to stretch or squish the Y axis.

</details>

### Cellular Noise Parameters

<details>

<summary><strong>Additional Cellular Noise Parameters</strong></summary>

* <mark style="color:red;">`CellularJitterModifier (Jitter)`</mark>\
  Usually `0..1.0`\
  Controls the random jitter or distribution of cellular noise nodes, with 0 being a perfect grid, and 1 being maximally "random", without overlap. Values above 1 will start to overlap their neighbours.
* <mark style="color:red;">`CellularDistanceFunction (Distance)`</mark>\
  Controls the mathematical method used to determine the distance value for each point to its node.
  * <mark style="color:purple;">`Euclidean`</mark>
  * <mark style="color:purple;">`EuclideanSq (sq)`</mark>
  * <mark style="color:purple;">`Manhattan (man)`</mark>
  * <mark style="color:purple;">`Hybrid`</mark>
  * <mark style="color:purple;">`Minkovski1 (m1)`</mark>
  * <mark style="color:purple;">`Minkowvki4 (m4)`</mark>
  * <mark style="color:purple;">`Minkowski99 (m99)`</mark>
  * <mark style="color:purple;">`Rounded (round)`</mark>
* <mark style="color:red;">`CellularReturnType (DistReturn)`</mark>\
  Controls how the distance value is modified prior to being returned.\
  All Distance2\* values refer to the 2nd closest node instead of the closest.
  * <mark style="color:purple;">`CellValue (cell)`</mark>
  * <mark style="color:purple;">`Distance (1)`</mark>
  * <mark style="color:purple;">`DistanceSquared (sq)`</mark>
  * <mark style="color:purple;">`DistanceInverse (inv)`</mark>
  * <mark style="color:purple;">`DistanceLog (log)`</mark>
  * <mark style="color:purple;">`DistanceExp (exp)`</mark>
  * <mark style="color:purple;">`Distance2 (2)`</mark>
  * <mark style="color:purple;">`Distance2Add (2add)`</mark>
  * <mark style="color:purple;">`Distance2Add (2sub)`</mark>
  * <mark style="color:purple;">`Distance2Add (2mul)`</mark>
  * <mark style="color:purple;">`Distance2Add (2div)`</mark>
  * <mark style="color:purple;">`Distance2Sq (2sq)`</mark>
  * <mark style="color:purple;">`Distance2Inv (2inv)`</mark>
  * <mark style="color:purple;">`Distance2Log (2log)`</mark>
  * <mark style="color:purple;">`Distance2Exp (2exp)`</mark>
  * <mark style="color:purple;">`Edge`</mark>
  * <mark style="color:purple;">`Rounded (round)`</mark>
  * <mark style="color:purple;">`NoiseLookup (noise)`</mark>\
    **Additional Noise Lookup Parameters:**
    * <mark style="color:red;">`CellularNoiseLookup (Lookup)`</mark>\
      When using the NoiseLookup return type, this controls the underlying noise to overlay the cellular noise upon.
      * <mark style="color:purple;">`Perlin (per)`</mark>
      * <mark style="color:purple;">`OpenSimplex2 (simplex)`</mark>
      * <mark style="color:purple;">`OpenSimplex2S (smooth)`</mark>
      * <mark style="color:purple;">`Value (val)`</mark>
      * <mark style="color:purple;">`ValueCubic (cubic)`</mark>
      * <mark style="color:purple;">`White`</mark>
      * <mark style="color:purple;">`Cellular (vor)`</mark>
    * <mark style="color:red;">`CellularNoiseLookupFrequency (DistReturn)`</mark>\
      Controls the frequency of the underlying noise.

</details>

### Shard Noise Parameters

<details>

<summary>Additional Shard Noise Parameters</summary>

* <mark style="color:red;">`Sharpness (Sharp)`</mark>\
  Usually `0..1.0`\
  Controls the pattern sharpness for Shard noise. Higher values have more defined edges within the pattern, whereas low values will appear more blurry.

</details>

### Fractal Noise Parameters

<details>

<summary>Fractal Noise Parameters</summary>

* <mark style="color:red;">`FractalType (Fractal)`</mark>\
  Sets the type of fractal noise to be used.
  * <mark style="color:purple;">`None (No)`</mark>
  * <mark style="color:purple;">`FBm`</mark>
  * <mark style="color:purple;">`Ridged`</mark>
  * <mark style="color:purple;">`PingPong (PP)`</mark>\
    **Additional PingPong Fractal Parameter:**
    * <mark style="color:red;">`PingPongStrength (PPStr)`</mark>

**If Fractal Type other than `None` selected:**

* <mark style="color:red;">`Octaves (Oct)`</mark>\
  Sets the number of layers of fractal noise to be used.
* <mark style="color:red;">`Lacunarity (Lac)`</mark>\
  Sets the scale of each fractal layer. Values >1 will effectively increase the frequency for each layer, values <1 will effectively reduce the frequency for each layer.
* <mark style="color:red;">`Gain`</mark>\
  Sets the relative strength of each fractal layer. Values <1 will decrease in strength for each layer, values >1 will increase.
* <mark style="color:red;">`WeightedStrength (Weighted)`</mark>\
  Sets the responsiveness of each layer's strength to the noise value.

</details>

### Domain Warp Parameters

<details>

<summary>Domain Warp Parameters</summary>

* <mark style="color:red;">`DomainWarpType (Warp)`</mark>\
  Sets the type of domain warping to be used.
  * <mark style="color:purple;">`None (No)`</mark>
  * <mark style="color:purple;">`BasicGrid (Grid)`</mark>
  * <mark style="color:purple;">`OpenSimplex2 (Simplex)`</mark>
  * <mark style="color:purple;">`OpenSimplex2Reduced (Reduced)`</mark>
  * <mark style="color:purple;">`Flow`</mark>
  * <mark style="color:purple;">`Turbulence (Turb)`</mark>

**If Domain Warp Type other than `None` selected:**

* <mark style="color:red;">`DomainWarpFreq (WarpFreq)`</mark>\
  Sets the frequency for the domain warp.
* <mark style="color:red;">`DomainWarpOct (WarpOct)`</mark>\
  Sets the number of layers for the domain warp.
* <mark style="color:red;">`DomainWarpGain (WarpGain)`</mark>\
  Sets the relative strength of each domain warp layer.
* <mark style="color:red;">`DomainWarpAmp (WarpAmp)`</mark>\
  Sets the overall amplitude (strength) of the domain warp.
* <mark style="color:red;">`DomainWarpFrac (WarpFrac)`</mark>\
  Sets the domain warp specific fractal type to be used.
  * <mark style="color:purple;">`None (No)`</mark>
  * <mark style="color:purple;">`DomainWarpIndependent (ind)`</mark>
  * <mark style="color:purple;">`DomainWarpProgressive (prog)`</mark>
* <mark style="color:red;">`DomainWarpLacunarity (WarpLac)`</mark>\
  Sets the scale of each domain warp layer.

</details>



## Examples

**`Value(Seed:123,Freq:0.04)`**

<figure><img src="../.gitbook/assets/2024-01-10_20.38.35.png" alt=""><figcaption></figcaption></figure>

**`Cellular(Distance:Euclidean,DistReturn:NoiseLookup,Lookup:Perlin,LookupFreq:0.2,Freq:0.1)`**

<figure><img src="../.gitbook/assets/2024-01-10_20.41.26.png" alt=""><figcaption></figcaption></figure>
