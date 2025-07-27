## Instructions
  Zip file link - https://drive.google.com/file/d/1KMttw3LFp2I17lCUW2S8elnZhwf7WGV_/view?usp=share_link
  Modify the compiler in makefile to c++11 (already done).
  Make in Libraries folder.
  java program in com.iiitb.imageEffectApplication.

## Usage

  Libraries - 

    1. Brightness : 
    The function takes in an image and a float value amount as input parameters. If amount is greater than 100, the function increases the brightness of the image by multiplying the RGB values of each pixel by (amount/100). If the resulting value is greater than 255, it is set to 255. If amount is less than 100, the function decreases the brightness of the image by multiplying the RGB values of each pixel by (amount/100).

    2. Contrast : 
    The function adjusts the contrast of the image by subtracting 128 from the RGB values of each pixel, multiplying the result by (amount/100), and then adding 128 back to the result. The function also ensures that the RGB values of each pixel are within the range of 0 to 255.

    3. Flip : 
    The function takes in an image and two integer values horizontalFlipValue and verticalFlipValue as input parameters. If horizontalFlipValue is 1, the function flips the image horizontally by reversing the order of pixels in each row of the image. If verticalFlipValue is 1, the function flips the image vertically by reversing the order of rows in the image.

    4. Grayscale : 
      The function converts each pixel of the image to grayscale by calculating the weighted average of the red, green, and blue values of the pixel. The resulting value is then assigned to the red, green, and blue values of the pixel to create a grayscale image.

    5. Hue Saturation : 
      The function applies the given hue and saturation values to the image by converting each pixel’s RGB value to HSV value, modifying the hue and saturation values, and then converting the HSV value back to RGB value. Finally, the modified image is returned as output.

    6. Invert : 
    The function creates a copy of the input image and inverts the colors of each pixel in the copied image by subtracting the RGB values of each pixel from 255. The modified image is returned as output.  

    7. Rotation : 
      The code rotates an image that takes that image and an integer value as input parameters. The function rotates the input image by 90 degrees clockwise for each increment of the input value. The rotated image is returned as output.

    8. Sepia : 
      The function applies a sepia filter to the input image by modifying the RGB values of each pixel using the following formulae: tr = 0.393 * r + 0.769 * g + 0.189 * b, tg = 0.349 * r + 0.686 * g + 0.168 * b, and tb = 0.272 * r + 0.534 * g + 0.131 * b. 

    9. Sharpen : 
      The code Sharpens an image that takes that image and a float value as input parameters. The function applies a sharpen filter to the input image by convolving the image with a 3x3 kernel. The kernel is defined as {-1, -1, -1}, {-1, 9, -1}, {-1, -1, -1}. Finally, the modified image is returned as output.

    10. Gaussian Blur : 
      The code implements the Gaussian blur algorithm. It takes an input image and a radius as arguments and returns a blurred version of the image. The algorithm first creates a Gaussian kernel with the given radius and then convolves it with the input image to produce the blurred output. The amount of blurring is controlled by the radius parameter, with larger values resulting in more blur.

  effectsImplementation package

    This package has the class files for all the effects. Each class effect implements an interface from the baseEffects package based on the type of parameter that the effect requires. Each class has two methods; one to set the parameters and the other to apply the effect and to log. Setting parameter throws IllegalParameterException whenever incorrect parameters or option names are given. It is caught in PhotoEffectService.java file. The apply method calls the methods in libraryInterfaces package, which internally call the cpp methods. It is also here that we log the effect on an image using the 'addLog()' method.

  Logging Service

    In the photoeditor website, when we apply an effect to the image, we call the 'addLog()' method of the 'LoggingService' class. We store the newly created 'LogModel' 
    instances in a predefined list. When we click on the ' logs page ' , we call the 'getAllLogs()' method of the 'LoggingService' class, this returns all the elements 		contained in the list. The two types of filters present are by time and by effect name which have their own function. To filter by effect name, we compare the strings.
    To filter by time, we convert the 'timestamp' string to 'LocalDateTime' datatype timestamp and compare the different timestamps and add the logs which satisfy these 	conditions to a new list and finally return this list. 

## Contributions

  Anirudh - Package, Exception handling, brightness effect
  Sai - Logging service, rotation effect and Report
  Sujit - Contrast effect, gaussian blur effect and Package
  Harshith -  Grayscale effect, sharpen effect and Logging service
  Karthikeyan - Flip effect, sepia effect and Package
  Surya - Invert effect, Hue & Saturation effect and Report