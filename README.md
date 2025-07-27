# ImageEffectApplication - Backend Libraries

This backend library provides core C++11 implementations of advanced image effects for the ImageEffectApplication project. The libraries are modular, efficient, and fully extensible, ensuring maintainability and ease of addition for future effects.

## Project Structure (`Libraries/` Folder)

```bash
Libraries/
├── BrightnessLibrary/
│   ├── Brightness.cpp
│   ├── Brightness.h
│   ├── BrightnessInterface.cpp
│   ├── BrightnessLib.so
│   └── libraryInterfaces_BrightnessInterface.h
├── ContrastLibrary/
├── FlipLibrary/
├── GaussianBlurLibrary/
├── GrayscaleLibrary/
├── HueSaturationLibrary/
├── InvertLibrary/
├── RotationLibrary/
├── SepiaLibrary/
├── SharpenLibrary/
├── libraryInterfaces/
├── Pixel.h
└── Makefile
```

## Image Effects and Their Functionality

### 1. Brightness
- **Function**: Adjusts the brightness of the image.
- **Usage**: Multiplies pixel RGB values by (`amount`/100). If `amount > 100`, increases brightness (values capped at 255). If `amount < 100`, decreases brightness.

### 2. Contrast
- **Function**: Modifies the image contrast.
- **Usage**: For each pixel, subtract 128 from RGB, multiply by (`amount`/100), add 128 back. Values are clamped from 0–255.

### 3. Flip
- **Function**: Flips the image horizontally, vertically, or both.
- **Usage**: 
  - If `horizontalFlipValue == 1`, reverse pixels in every row.
  - If `verticalFlipValue == 1`, reverse the order of rows.

### 4. Grayscale
- **Function**: Converts an image to grayscale.
- **Usage**: Sets each pixel's RGB values to the luminance-weighted average of the original RGB.

### 5. Hue & Saturation
- **Function**: Alters hue and saturation.
- **Usage**: Convert each pixel RGB to HSV, adjust hue and saturation, then convert back to RGB.

### 6. Invert
- **Function**: Inverts all colors in the image.
- **Usage**: Each pixel color set to `255 - current_value` for every RGB channel.

### 7. Rotation
- **Function**: Rotates image in 90° increments.
- **Usage**: Rotates clockwise by 90° for each unit in the input parameter.

### 8. Sepia
- **Function**: Applies a sepia tone filter.
- **Usage**:
  
  tr = 0.393*r + 0.769*g + 0.189*b
  tg = 0.349*r + 0.686*g + 0.168*b
  tb = 0.272*r + 0.534*g + 0.131*b
  
  RGB values are clamped at 255.

### 9. Sharpen
- **Function**: Sharpens the image.
- **Usage**: Applies a 3x3 convolution kernel:
  
  -1, -1, -1
  -1,  9, -1
  -1, -1, -1
  
  Resulting values are clamped from 0–255.

### 10. Gaussian Blur
- **Function**: Blurs the image using a Gaussian kernel.
- **Usage**: A kernel is computed with the specified radius, convolved with the image to produce blur. Higher radius → more blur.

## Exception Handling

All effects validate input parameters and handle incorrect usage via custom exceptions. Incorrect values (e.g., unsupported parameters, wrong option names) are reported safely for stable operation.

## Compilation

1. Ensure C++11 compiler is set (Makefile already configured).
2. From the `Libraries` folder, run:
    
    make
    
   This compiles all effect modules and generates the dynamic library files.

## Extensibility

- Each effect is encapsulated in its own sub-directory for clarity and maintainability.
- Adding new effects requires following the folder/template style used for existing modules.