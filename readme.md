ML based Mobile application to detect proper Muzzle


ML based Mobile application consisted with a machine learning model, which is previously trained for the business solution.

Pipe lining machine learning model to flutter mobile application:

Required dependencies:
	In our case, our application will do muzzle detection, which will use camera as live feed and also detect muzzle from offline images. And machine learning model will be tensorflow lite, which is specially used for mobile and embedded system.
These are flutter dependencies.

camera: ^0.10.4
image_picker: ^0.8.7+3
tflite: ^1.1.2

Workflow:

	![image](https://github.com/s4ki3f/muzzle_detector_app/assets/29111757/67d7821c-1697-48de-a1ef-9723d3ea8a91)

	Camera to pick images: the flutter camera plugin that saves a frame as a CameraImage. This can be converted to the Image class.

	Preparing model where tflite data will be assigned and labeled: tesorflow lite model and model.data need to be saved in the asset folder and later on will be assigned from there. And this labeld file(in txt file) has all class information and model hold the memory of those class data

	Image pre-processing: Raw images captured from the camera or incepted frame from the live feed images has resolution which is quite larger than required dimension. It has to be 300*300 
	Feed the image to the logic and prediction: Before creating the logic for predicting,
It is recommended to apply hardware acceleration features while initializing a TensorFlow Lite model to speed up the model's prediction calculations.
TensorFlow Lite delegates are software modules that accelerate machine learning model execution on mobile devices by utilizing specialized processing hardware such as Graphics Processing Units (GPUs), Tensor Processing Units (TPUs), and Digital Signal Processors (DSPs). It is suggested, but not needed, to use delegates when running TensorFlow Lite models.
With detectors produced on the main thread and utilized on a background thread, the CPU and NNAPI delegates are used, but the thread that initialized the detector must use the GPU delegate.
Using the tensor buffer and interpreter in the inference is needed to store the data. Or can be use tensor flow task to maintain dataflow.

	Presentation: prediction results on live feed and and local feed images will be analized and showcase the results in, image can be accepted or cannot be accepted(if all the requirements do not match). And for live feed it will asked the user to trigger shutter button or can be automated when it matches the frame and got accepted.


Tensorflow lite model: ![muzzle_detection.tflite](https://drive.google.com/file/d/1_T4xMNVAsscqOpN9CQOvxEoOayWNP2da/view?usp=share_link)
(this tflite model is trained on muzzle detection and can be downloaded from the drive link attached.)
Class labeled file: ![detected_class.txt](https://drive.google.com/file/d/1aY_FRdyRhgG1NsNbfSU5SXkw8e3jf7It/view?usp=share_link)
(this txt file contain class name to pass it through allong with tflite model)


Reference work and repos:

	https://www.tensorflow.org/lite/android/tutorials/object_detection
	https://github.com/am15h/object_detection_flutter
	https://github.com/krissnawat/cat-dog-detector-flutter
	https://pub.dev/packages/camera
	https://pub.dev/packages/image_picker
	https://pub.dev/packages/tflite_flutter
https://pub.dev/packages/tflite_flutter_helper	

