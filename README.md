This is an ImageJ macro designed to batch process TIFF image stacks within a specified directory and its subdirectories. Here's a breakdown of how to use it and what it does:

Purpose:

The macro automates the following image processing steps:

Bleach Correction: Corrects for photobleaching in time-lapse image stacks.
Denoising: Reduces noise in the images.
16-bit Conversion: Ensures the processed images are saved in 16-bit TIFF format.
How to Use:

Install ImageJ (or Fiji):

If you don't have ImageJ or Fiji (Fiji is ImageJ with many plugins pre-installed), download and install it from the official website.
Open the Macro Editor:

In ImageJ or Fiji, go to "Plugins" -> "New" -> "Macro". This will open the Macro Editor.
Copy and Paste the Code:

Copy the entire code provided and paste it into the Macro Editor.
Save the Macro:

Go to "File" -> "Save As..." and save the macro with a .ijm extension (e.g., BatchProcessTIFFs.ijm).
Run the Macro:

Go to "Run" -> "Run".
A dialog box will appear asking you to "Choose a Directory".
Select the folder containing the TIFF image stacks you want to process.
Click "OK".
Processing:

The macro will then:
Recursively search the selected folder and its subfolders for .tif files.
Open each TIFF file.
Apply bleach correction (if the image is a stack).
Apply denoising using the "PureDenoise" plugin.
Convert the image to 16-bit.
Save the processed image with a new filename (e.g., originalFileName-acceptor-1.tif).
Close the original image.
Display a progress bar.
Print the total number of processed files to the ImageJ Log window.
Explanation of Code Sections:

requires("1.33s");: Ensures the macro runs on ImageJ versions 1.33s or later.
getDirectory("Choose a Directory");: Prompts the user to select the input directory.
setBatchMode(true);: Prevents ImageJ from displaying each image during processing, speeding up the process.
countFiles(dir);: Recursively counts the number of .tif files in the directory and its subdirectories.
processFiles(dir);: Recursively processes each .tif file.
processFile(path);:
Opens the specified TIFF file.
Extracts the base filename.
Applies bleach correction using an exponential multiplication (the k value controls the correction strength).
Applies denoising using the "PureDenoise" plugin (you can modify the plugin parameters).
Converts the image to 16-bit.
Saves the processed image.
Closes the original image.
Important Notes:

Bleach Correction:
The k value in the bleach correction section determines the strength of the correction. You'll need to adjust this value based on the severity of photobleaching in your images.
The bleach correction only works on image stacks. If an image is not a stack, it will be skipped.
Denoising:
The "PureDenoise" plugin parameters ('10 4') may need to be adjusted depending on the noise characteristics of your images.
Make sure you have the PureDenoise plugin installed.
Output Filenames:
The processed images are saved with the original filename followed by -acceptor- and a number. You can modify this naming convention.
Error Handling:
The macro includes basic error handling to check if the input directory exists.
It also warns if a single image is passed to the bleach correction.
Plugin Dependencies:
This macro requires the "PureDenoise" plugin to be installed. Make sure to install that plugin before running this macro.
Memory Considerations:
Processing large image stacks can consume a significant amount of memory. Ensure you have sufficient RAM.
This macro provides a convenient way to automate the processing of multiple TIFF image stacks in ImageJ. Remember to adjust the parameters to suit your specific image data.
