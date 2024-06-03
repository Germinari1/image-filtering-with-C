# Image filtering with C
This program is a command-line tool that applies various filters to bitmap (BMP) image files. The filters available are grayscale, reflection, blur, and edge detection. The program takes two arguments: a flag specifying the desired filter and the names of the input and output files.

## Usage

To use the program, run the following command:
```txt
./filter [flag] infile outfile
```
Replace `[flag]` with one of the following filter options:

- `b`: Blur filter
- `e`: Edge detection filter
- `g`: Grayscale filter
- `r`: Reflection filter

Replace `infile` with the name of the input BMP file, and `outfile` with the desired name for the output file.

## Requirements

This program assumes that the input BMP file is a 24-bit uncompressed BMP 4.0 image. Other file formats are not supported. The good news is that no external/non-native libraries are used :)

## Filters

### Grayscale

The grayscale filter converts the image to shades of gray by setting the red, green, and blue values of each pixel to the same value, which is the average of the original red, green, and blue values.

### Reflection

The reflection filter creates a horizontal mirror image by reflecting the pixels around the middle of the image.

### Blur

The blur filter applies a box blur to the image by computing the average of each pixel and its surrounding pixels. For pixels at the edge of the image, only the available neighboring pixels are considered.

### Edge Detection

The edge detection filter applies the Sobel operator to the image, highlighting edges by computing the approximations of the derivatives for each pixel.

## Implementation Details

The program is written in C and uses the following helper functions defined in `helpers.h`:

- `grayscale(int height, int width, RGBTRIPLE image[height][width])`: Applies the grayscale filter.
- `reflect(int height, int width, RGBTRIPLE image[height][width])`: Applies the reflection filter.
- `blur(int height, int width, RGBTRIPLE image[height][width])`: Applies the blur filter.
- `edges(int height, int width, RGBTRIPLE image[height][width])`: Applies the edge detection filter.

The `main` function handles command-line argument parsing, file I/O, and calls the appropriate filter function based on the provided flag.

## Example

To apply the grayscale filter to an input file `infile.bmp` and save the result as `outfile.bmp`, run:
```txt
./filter g infile.bmp outfile.bmp
```
This will create a new file `outfile.bmp` with the grayscale version of the input image.
