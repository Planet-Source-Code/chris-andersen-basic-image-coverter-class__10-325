<div align="center">

## Basic Image Coverter Class


</div>

### Description

This is a class that can turn any bitmap based image format into either, bmp, jpg, gif, tif, or png formats. It also includes setting the quality for Jpg type images. See the code in the module section for example usage. To compile this code, at the command line type vbc image.vb /r:system.drawing.dll . I will add more capabilities in the future.

IMPORTASNT NOTE.. add an extra 's' to the words Clas. Sorry but I had to remove the s because PSC's really bad parsing for bad words saw the last three letters and wouldnt let me post it..Very bad form PSC!
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Chris Andersen](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/chris-andersen.md)
**Level**          |Beginner
**User Rating**    |4.8 (29 globes from 6 users)
**Compatibility**  |VB\.NET
**Category**       |[Graphics/ Sound](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics-sound__10-15.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/chris-andersen-basic-image-coverter-class__10-325/archive/master.zip)





### Source Code

```
Imports System
Imports System.Drawing
Imports System.Drawing.Imaging
Module App
	Sub Main()
		Dim tst As New ImageConverter
		tst.ImagePath = "c:\ufr1.bmp"
		tst.ImageType = tst.ImageType.Gif
		tst.Quality = 100
		tst.ConvertImage()
	End Sub
End Module
Public Clas ImageConverter
	Public Enum enumImageTypes
		Bitmap = 0
		Jpeg = 1
		Gif = 2
		Tiff = 3
		Png = 4
	End Enum
	Public ImagePath As String
	Public ImageType As enumImageTypes
	Public Quality As Integer
	Public Sub ConvertImage()
		Dim newBitmap As Bitmap = New Bitmap(ImagePath)
		Dim imgCodecs() As ImageCodecInfo = ImageCodecInfo.GetImageEncoders()
		' Set quality Parameter for the Jpeg codec
		Dim imgParams As EncoderParameters = New EncoderParameters(1)
		Dim imgQuality As EncoderParameter = New EncoderParameter(System.Drawing.Imaging.Encoder.Quality, Quality)
		Dim imgExt As String
		' Set quality
		imgParams.Param(0) = imgQuality
		'Get file extension of codec
		imgExt = imgCodecs(ImageType).FilenameExtension
		imgExt = imgext.SubString(1, imgExt.Length - 1)
		newBitmap.Save(ImagePath.SubString(0, ImagePath.Length - 4) + imgExt, imgCodecs(ImageType), imgParams)
		newBitmap.Dispose()
	End Sub
End Clas
```

