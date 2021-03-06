# PPTToImgConverter 
This is a library that can convert slideshow (ppt or pptx format) into images (jpg, png, bmp or wbmp format) .
It's based on Apache POI，but with images of higher quality and simplier apis.
What you need to use the library，is just importing the dependencies and the single class.

这个工具类可以将ppt或者pptx文件转换为图片（支持4中格式jpg、png、bmp和wbmp）。
它基于Apache poi，但转换图片质量更高，api更加简洁。
使用它，仅需导入依赖和唯一个一个类`PPTToImgConverter`即可

# Demo
Some examples to show how to use this.
这是一些展示如何使用的小例子
```java
/**
 *A simple demo, all slides will be converted, and the resolution of images is consistent with that of origin slideshow.
 *简单例子，以自身分辨率输出ppt的每一页
 */
// set the parent directory of converted images, it's necessary. 设置图片输出目录。
        PPTToImgConverter.dir("E:/testppt")
                //select a file or folder. 选择一个文件或者文件夹。
                .file("E:/test.pptx")
                //start the conversion. 开始转换。
                .convert();

/**
 *A demo with more configurations.
 *一个稍微复杂点的例子。
 */
//set the parent directory of converted images. 设置图片输出目录。
        PPTToImgConverter.dir("E:/testppt")
                //select multiple files or folders.设置多个文件或者文件夹。
                .files(new String[]{"E:/pptFolder","E:/test.ppt"})
                //set the start position. 设置起始页码。
                .from(0)
                //set the end position, note that the end page will be converted，-1 means last page.
                //设置结束页码，-1表示倒数第一页，结束页码也会被转换。
                .to(-1)
                //set the width of resolution. 设置图片分辨率宽度。
                .width(400)
                //set the height of resolution. 设置图片分辨率高度。
                .height(300)
                //set the format of images. 设置图片格式
                .imgFormat(PPTToImgConverter.PNG)
                //start the conversion. 开始转换。
                .convert();

/**
 *other apis
 *note the scale dose not influence the resolution of final images, and it's unnecessary to set.
 *其他例子
 */
//set the parent directory of converted images. 设置图片输出目录。
        PPTToImgConverter.dir("E:/testppt")
                //set the scale of tmp images, not the final images!!!. 设置中间图片的放大倍数，根据自己需要进行尝试
                .scale(3)
                //select a file or folder. 选择一个文件或者文件夹。
                .file("E:/pptFolder")
                //set the compression ratio and it will be invalid once width or height set.
                //设置压缩比例，注意一旦你设置了宽度或者高度，则该设置无效。
                .ratio(0.500)
                //start the conversion of first page. 开始转换，只转换第一页。
                .convertFirstPage();
```
# Dependencies
```
<!-- 操作ppt所需依赖 manipulate slideshow -->
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi</artifactId>
            <version>4.1.0</version>
        </dependency>
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi-ooxml</artifactId>
            <version>4.1.0</version>
        </dependency>
        <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi-scratchpad</artifactId>
            <version>4.1.0</version>
        </dependency>

        <!-- 压缩图片 compress image -->
        <dependency>
            <groupId>net.coobird</groupId>
            <artifactId>thumbnailator</artifactId>
            <version>0.4.8</version>
        </dependency>
```
