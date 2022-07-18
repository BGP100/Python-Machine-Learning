<a href="/v3/ML-Intro/Neuronal-Networks.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/ML-Intro/Running-Your-Model.md">Next &gt;</a>
<hr>
<a href="https://teachablemachine.withgoogle.com/">Teachable Machine</a> is a google machine learning website that lets you collect data into datasets by snapping photos with your webcam or recording audio. This lets you create and train machine learning models without the overhead of creating data processing code or manually setting up a neural network.
<br>
Teachable Machine is perfect for models with small datasets and simple tasks. The example below tests whether the user in the webcam is giving a thumbs-up or thumbs-down.
<br>
<img src="https://i.imgur.com/zhWxQdI.gif">
<br>
<a href="https://i.imgur.com/zhWxQdI.gif">Click here if it doesn't load</a>
<h1>What is a Machine Learning Model?</h1>
Machine learning works by feeding data into a computer program, which uses that data to adjust its parameters and learn how to complete a task.
<br>
The Model in a Machine Learning program is the combination of mathematical functions and parameters that the program updates as it learns. This will often include a Neural Network - a series of connected functions and parameters that are well suited to adapting to various tasks.
<br>
Models are built and trained for different tasks, so the data that each model reads and the output that they produce will vary based on the model's purpose. Teachable Machine's models are primarily used for Classification problems - deciding which of a number of predetermined classes an input fits into. The model shown in the gif above is classifying whether the current webcam input is a thumbs-up (Yes) or a thumbs-down (No).
<br>
You can use Teachable Machine to train your own model to classify webcam input based on data you collect. In this lesson, you'll use Teachable Machine to train a model to recognize the hand poses in Rock Paper Scissors.
<h1>Creating a Project</h1>
First, you'll need to create a new Teachable Machine project.
<br>
1. Open Teachable Machine and select Image Project to create a new image classification project
<br>
2. In the pop-up click Standard image model to create your new model.
<br>
<img src="https://i.imgur.com/shGOxgu.jpg">
<br>
On the left of the project workspace, you can edit the categories your model will attempt to classify.
<br>
3. Click the pencil next to each category to rename each class:
Rename Class 1 to "Rock" and Class 2 to "Scissors".
<br>
4. Click Add a class to add new classes: Add two new classes and name them "Paper" and "None".
<br>
<img src="https://i.imgur.com/4QvmNqF.jpg">
<hr>
Rock:
<br>
<img src="https://i.imgur.com/2W9cDdQ.jpg">
Paper:
<br>
<img src="https://i.imgur.com/TcF8tZG.jpg">
Scissors:
<br>
<img src="https://i.imgur.com/DDBRh1Y.jpg">
None:
<br>
<img src="https://i.imgur.com/pMqCity.jpg">
<h1>Data Collection</h1>
Now that your classes are set up, you need to collect the data your machine learning model will use to learn.
<br>
The more data you provide for the model, the better it will be able to learn its job. You'll collect images via your webcam that will form the basis of your dataset.
<br>
1. Click Webcam in the Rock class to enable your webcam for data collection
<br>
2. Get ready to make the Rock hand sign, then click and hold Hold to Record to automatically take a series of images of your Rock hand sign. 
<br>
3. Move your hand around a bit and get some slightly different angles of the sign.
<br>
4. Repeat this process for each of the different hand signs, including None, where you'll hold up no hand signs.
<br>
<img src="https://i.imgur.com/p27cTvQ.gif">
<br>
<a href="https://i.imgur.com/p27cTvQ.gif">Click here if it doesn't load</a>
<br><br>
A good dataset is the foundation of an effective machine learning model. The more varied data you provide for each of the classes, the better the model will be able to detect each of the different classes. Now that you've collected your data, you can train the model.
<h1>Training</h1>
Behind the scenes, Teachable Machine is feeding your data for each class into the neural network, which then attempts to guess the correct class for each image. Based on comparing the guesses to the actual correct class for the image, the network adjusts its parameters. By repeating this process and adjusting for each image in the dataset, the model slightly improves its ability to guess the class of a given input.
<br>
1. Click Train Model to start processing the data and training the model. 
<br>
2. Wait a 30 seconds to 1 minute for it to process. "Don't close the window or change the tab while it's running!"
<br>
3. Once training finishes, use your webcam to preview the results and see a live feed of the prediction your model is making for the current webcam image.
<br>
<img src="https://i.imgur.com/TuxDBa0.jpg">
<br>
You've got a trained model, but it's probably not perfect at its job! You can improve it by identifying issues and providing more training data.
<h1>Tuning the Model</h1>
Improving the quality of the provided model allows your network to be more effective.
<br>
1. Test your model in the preview window with each of the different poses.
<br>
2. Keep written notes: each time the model is making an incorrect prediction, take note of what was confusing.
<br>
3. Try to find an incorrect reading for each class and write down what data might be missing for that particular variation of the pose.
<br>
The example below shows one incorrect reading a model might make:
<br>
<img src="https://i.imgur.com/5FtfyO8.jpg">
<br>
4. Return to the data section on the left and use the webcam recorder to create more data. Try using poses based on the issues you identified to fix any model issues you found.
<br>
<img src="https://i.imgur.com/0UEfuMK.jpg">
<br>
5. Click Train Model to retrain your model with the added data.
<br>
<img src="https://i.imgur.com/HeKV8da.jpg">
<br>
You can keep improving and tuning your model by repeating this process. Once you're satisfied with your changes and training, congratulations! You've created your own dataset, used it to train a neural network, and refined the results by improving the quality of your data!
<br>
This process is a simplified version of exactly what machine learning researchers do to create, train, and improve their machine learning models for any number of applications.
<h1>Recap</h1>
Machine learning models work by using input data to adjust and improve parameters over repeated tests. With quality training data, the model can learn to accomplish a variety of tasks, like classifying the contents of images.
<ul>
  <li>Collect data from the webcam for each class you want to classify.</li>
  <li>Train your model to learn from the data you collected.</li>
  <li>Test the results and improve your data via experimentation.</li>
</ul>
