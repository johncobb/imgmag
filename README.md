Instructions of common ImageMagick usage such as resizing, exporting formats, cropping, splicing, appending etc. 

### Install steps using Mac OS:


 * Run the following terminal commands:

			brew install imagemagick
			brew install gs
* Check that both ImageMagick and GhostScript installed correctly:
	
			convert -info
 			gs -info

* If one or both of the previous commands failed with either program not installing common  	 problems can often be solved with:
		
			brew -doctor

  
## Usage

#### Further info can be found at:

<https://www.imagemagick.org/Usage/>

**Hint:** A well-organized file structure with folders for input/output files and folders for various file types highly recommended.

* The common syntax for ImageMagick goes roughly along the lines of:

| Call convert to start. | FileName/type for input pic   | Crop/append/splice commands   | Size, crop amount etc  | Output file name/type  |
|:----------------------:|:-----------------------------:| :----------------------------:| :---------------------:| :---------------------:|
| convert                | inputFileName.type            | -argument                     | arg parameters         | outputFile.type        |


#### Examples of converting pdf to different image formats

##### pdf to tiff

`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/tiff/out.tiff`

##### pdf to png

`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/png/out.png`

##### pdf to jpeg

`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/jpeg/out.jpeg`

#### Explanation:
-The density command sets exported image DPI (dots per square inch) 300 is a standard for this project

-The depth command sets the kind of floating point type. -depth value of 32 or less is normal "floats". If the picture is set to -depth 64 then doubles are used for the floating point data written to, or read from, the image file format.

-The strip command removes any image profiles

-The background * backgroundColor * command sets the background. For this project * white * is the background

-The alpha command along with -matte are options that set values having to do with transparency. For this project -alpha off will be standard

#### Cropping contents of an image

##### Reference:

<http://www.imagemagick.org/Usage/crop/>

`convert image_name -crop pixelsX x pixelsY + pixelOffsetX + pixelOffsetY outputfile`

`convert out/tiff/out.tiff -crop 350x2550+25+0 out/jpg/out/out.jpg`

Alternatively percantages can replace pixels. Here is an example that will produce a cropped image similar to the above:
convert out/tiff/out.tiff -crop 11%x100%+25+0 out/jpg/out/out,jpeg

Examples:

A. Changing pixelsX will add/subtract pixels from the right side (e.g. -100 or +100)

B. Changing pixelsY will add/subtract pixels from the bottom (e.g. -100 or +100)

C. Changing pixelOffsetX will move the cropped section of the picture towards the left or right (e.g. -100 or +100)

D. Changing pixelOffsetY will move the cropped section of the picture up or down (e.g. -100 or +100)


### Combining cropped images into a single file
References:

<http://www.imagemagick.org/Usage/crop/#splice>

<https://www.imagemagick.org/Usage/basics/#example>

<https://raywoodcockslatest.wordpress.com/2017/02/23/imagemagick-append/>

##### Instructions: 

With cropped images combining them is as simple as listing the desired pictures and calling the +append command... like so:

`convert folder/folder/fileName.type folder/folder/fileName.type +append combinedFile.type`

Example with more than 2 pictures:

`convert out/jpeg/out-4.jpg out/jpeg/out-5.jpg out/jpeg/out-6.jpg +append combined.tiff`

### Putting it all together

##### Example conversion pdf to image

`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/tiff/out.tiff`

##### Extract column1

`convert out/tiff/out.tiff -crop 350x2550+25+0 out/jpeg/column1.jpeg`

or

`convert out/jpeg/out.jpg -crop 11%x100%+15+0 out/tiff/column1.tiff`

##### Extract column2

`convert out/tiff/out.tiff -crop 350x2550+1450+0 out/jpeg/column2.jpeg`

or

`convert out/jpeg/out.jpg -crop 11%x100%+1450+0 out/tiff/column2.tiff`

##### Append column 1 and 2

`convert out/jpeg/column1.jpeg out/jpeg/column2.jpeg +append out/jpeg/combined.jpeg`

or

`convert out/tiff/coumn1.tiff out/tiff/column2.tiff +append out/tiff/combined.tiff`
