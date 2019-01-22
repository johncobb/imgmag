
# Image manipulation with ImageMagick

### mac os install via brew
`brew install imagemagick`
`brew install gs`

### ubuntu linux install via apt
`sudo apt install imagemagick`

### Examples of converting pdf to different image formats
#### pdf to tiff
`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/tiff/out.tiff`
#### pdf to png
`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/png/out.png`
#### pdf to jpeg
`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/jpeg/out.jpeg`

### Cropping contents of an image
##### http://www.imagemagick.org/Usage/crop/
#### convert image_name -crop pixelsX x pixelsY + pixelOffsetX + pixelOffsetY outputfile
`convert out/tiff/out.tiff -crop 600x1800+100+200 out/jpeg/out/out.jpeg`

### Splicing cropped images into a single file
#### TODO: research splicing column1 thru column(n) into one file
#### http://www.imagemagick.org/Usage/crop/#splice


### Putting it all together
#### example conversion pdf to image
`convert -density 300 pdf/example.pdf -depth 8 -strip -background white -alpha off out/tiff/out.tiff`

#### extract column1
`convert out/tiff/out.tiff -crop 400x1800+10+200 out/jpeg/column1.jpeg`
#### extract column2
`convert out/tiff/out.tiff -crop 200x1800+1500+200 out/jpeg/column2.jpeg`

### splice column1 thru column(n) to one file
#### TODO:


