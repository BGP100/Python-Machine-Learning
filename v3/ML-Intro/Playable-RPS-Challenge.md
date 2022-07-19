<a href="/v3/ML-Intro/Running-Your-Models.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/ML-Intro/Teachable-Machine-Challenges.md">Next &gt;</a>
<hr>
<h1>Adding Webcam Capture</h1>
You've got code now that runs your Teachable Machine model and outputs a result. Using the webcam, you can create a program that captures photos from your webcam for your model to test.
<br>
Google Colab offers code snippets for common tasks that allow you to implement functionality instantly, including capturing from the webcam.
<br>
Click the "&lt; &gt;" icon on the left sidebar of your Colab Notebook to open the Snippets window.
<br>
1. You'll see a sidebar open up with a filter search bar at the top.
<br>
2. In the filter field, search for "Camera Capture"
<br>
3. In the results, select the "Camera Capture" snippet. You'll see a couple of cells of python and javascript code appear.
<br>
4. Click the arrow icon to add the snippets to your project.
<br>
<img src="https://i.imgur.com/YCFq2b4.png">
<br>
5. Move the added cells up to the top of the notebook using the arrow buttons.
<br>
The first of the two cells declares a function that runs the javascript needed to open up and use your webcam with Colab.
<br>
The second cell will call that function to start up the webcam and create a small UI to take a photo and save it as "photo.jpg".
<br>
6. Run the cells to take a picture and have it save to your runtime.
<br>
You should be able to take photos with your webcam and see them show up in the file browser.
<h1>Using Photos for Rock Paper Scissors</h1>
Modify the filename to use your photo.
<br>
1. In the cell that runs your Keras model, change the line that loads the image to:
<pre>image = Image.open("photo.jpg")</pre>
2. Instead of printing the result at the end with the line <code>print(labels[np.argmax(prediction)])</code>,  save the result of argmax to track the choice:
<pre>choice = np.argmax(prediction)</pre>
3. Just below that, use numpy's random int function to have the computer pick a choice:
<pre>ai_choice = np.random.randint(3)</pre>
4. Once both choices are saved, use the strings from the labels list to display the choices:
<pre>print(labels[choice] + " vs \n" + labels[ai_choice])</pre>
<br>
<img src="https://i.imgur.com/YKMW3sE.png">
<br>
Now you've got choices made by the player based on the prediction from the neural network of your image and a randomly chosen option by the computer. Next up is figuring out who won.
<br>
5. First, if the player didn't hold up a hand sign that the model recognized, let them know.
<pre>
if choice == 3:
print("You didn't play anything! You lose.")
</pre>
6. Next, check if the AI won:
<pre>
elif (choice + 1) % 3 == ai_choice:
print("Computer wins!")
</pre>
7. Then, check if it's a draw:
<pre>
elif choice == ai_choice:
print("Draw!")
</pre>
8. Finally, if none of the above were true, then the player won:
<pre>
else:
 print("You win!")
</pre>
<img src="https://i.imgur.com/SdtRLdT.png">
<br>
Now if you run all the cells in your notebook, you've got a playable Rock Paper Scissors game that will prompt you to take a webcam photo then use it to play Rock Paper Scissors against the computer.
<h1>Recap</h1>
You can use Colab's code snippets to search for boilerplate code to use various features like the webcam. Combining that with your Keras code to load your model, you can make projects utilizing the models built with Teachable Machine.
<ul>
  <li>The "take_photo" function opens up a UI to take a webcam photo. Can you figure out how to take a second photo, save it, and use it instead of the AI decision?</li>
  <li>Can you make it so the computer always picks the winning gesture? What about so the computer always picks the losing gesture?</li>
</ul>
