# SmartCropper

简单易用的智能图片裁剪库，适用于身份证，名片，文档等照片的裁剪。 欢迎 start，follow。

## 支持特性

- 使用智能算法识别图片中的边框  
- 支持拖动锚点，手动调节选区  
- 使用透视变换裁剪并矫正选区

## 例子
下载Demo：[传送门](art/SmartCropperSample.apk)

### 智能选区：

![](art/smart_crop.png)

### 透视变换裁剪并矫正选区：

![](art/cropped.png)


### 拖动锚点，手动调节选区：

![](art/advance_crop.png)

### gif 动画（有点卡）：

![](art/smartcropper.gif)


## 接入

可以直接依赖 aar 文件夹下的 aar 文件，也可以 clone 项目，将 smartcropperlib 作为 Android 模块导入。之后有需要的话可以上传到仓库。   
另外根目录 libs 目录下是编译好的 native library，如果引入项目不想编译，可以直接使用。

注意：**不要混淆**

## 使用  

### 1. 布局：  
```xml
<me.pqpo.smartcropperlib.view.CropImageView   
        android:id="@+id/iv_crop"  
        android:layout_width="match_parent"  
        android:layout_margin="20dp"  
        android:layout_height="0dp"  
        android:layout_weight="1"/>  
```  

### 2. 智能选区：    

```java  
Point[] points = SmartCropper.scan(selectedBitmap);    
```  
在 native 层智能识别边框，返回的 points 是大小为4的数组，表示选区边框的四个顶点，依次为左上，右上，右下，左下。 

### 3. 设置给 CropImageView 展示

```java
ivCrop.setCropPoints(points);  
ivCrop.setImageBitmap(selectedBitmap);  
```
将选区顶点，需要显示的图片设置给 CropImageView 显示图片，绘制选区。 

### 3. 裁剪：

```java  
Bitmap crop = ivCrop.crop();  
```  
根据选区裁剪出选区内的图片，并使用透视变换矫正。

## API 说明

### SmartCropper 类：

#### 1. 扫描边框，大图下会比较耗时

```java
public static Point[] scan(Bitmap srcBmp)
``` 
返回值为大小为4的 Point 数组，表示选区边框的四个顶点，依次为左上，右上，右下，左下。

#### 2. 根据边框顶点裁剪，大图下会比较耗时

```java
public static Bitmap crop(Bitmap srcBmp, Point[] cropPoints)
```

### CropImageView 类：

#### 1. 设置裁剪边框锚点
```java
public void setCropPoints(Point[] cropPoints)
```

#### 2. 设置选区外的透明度
```java
public void setMaskAlpha(int mMaskAlpha)
```

#### 3. 设置是否显示辅助线
```java
public void setShowGuideLine(boolean showGuideLine)
```
#### 4. 设置选区边框线颜色
```java
public void setLineColor(int lineColor)
```
#### 5. 设置选区边框线宽度

```java
public void setLineWidth(int lineWidth)
```

#### 6. 根据用户选区裁剪图片

```java
public Bitmap crop()
```

#### 7. 根据指定顶点裁剪图片

```java
public Bitmap crop(Point[] points)
```

## Futures

1. 优化智能选区算法
2. CropImageView 选区放大镜效果
3. ...

---
如有问题可联系：pqponet#gmail.com, 也可提 ISSUE。  
我的博客：https://pqpo.me  


License
-------

    Copyright 2017 pqpo

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.




