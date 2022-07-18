<a href="/v3/Libraries/Graphs.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/ML-Intro/Neuronal-Networks.md">Next &gt;</a>
<hr>
A basic task for any neural network is classification: separating inputs into two groups, called classes.
<br>
For instance, you might want to separate emails into spam or non-spam, patients into those with or without a disease, or images into those of a car or not.  A label refers to a data point contained inside a specific class.
<br>
As a human, you can recognize and categorize some of these things. In the case of determining spam mail, you can classify a message into spam or not spam just by reading it.
<h1>Identifying Spam eMails</h1>
If the computer had to figure this out for itself, it wouldn't know what's important and what's not.
<br>
The goal is to create a model: a system that can predict which class a new data point is without knowing its label.  You do that by breaking our input data into features, the basic information underlying each data point.  Features are chosen to help you figure out the label as easily as possible.  There are lots of features to choose, and the challenge is to use the ones that will help the most.
<br>
For each data point, you'll need to know its features and its label.
<ul>
  <li><sub>The number of words in an email.  Spam is often overly wordy.  Spam emails sometimes go on very strange tangents; a lot of spam emails will consistently use run-on sentences that kind of don't get to the point very quickly because they're meant to just fill space instead of having actual information and also they don't use a lot of punctuation if any at all which makes it really difficult to read and will drain your brain pretty hard also it blends together the words into just one big soup of communication that drones on and on an...</sub></li>
  <li>How many WORDS are in ALL-CAPS?  Spam can be OVERLY EXCITED about things and over use CAPITAL LETTERS.</li>
  <li><b><i>Punctuation, maybe????  Spam sometimes uses too many exclamation marks!!!!</i></b></li>
</ul>
<h1>Getting it Wrong: Loss</h1>
Models are only helpful if they get their answers correct. When a data scientist makes a new model, they need to compute its loss: a number telling how often the model was wrong.
<br>
<img src="https://i.imgur.com/WcX1L0l.gif">
<br>
By measuring loss with a specific number, you can compare two models, and see which one is a better problem solver by finding the smaller loss.
<h1>Play with Neural Networks</h1>
The <a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=true&activation_hide=true">Neural Network Playground</a> lets you explore simple neural networks and see how they work.
<br>
<img src="https://i.imgur.com/WjqKZnX.jpg">
<h2>Examples</h2>
2-layer circle
<br>
<a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=2,2&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=true&ySquared=true&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=true&activation_hide=true">link</a>
<hr>
8-layer circle
<br>
<a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=2,2&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=true&ySquared=true&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=true&activation_hide=true](https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=2,2,1,2,2,2,1,2&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=true&xSquared=true&ySquared=true&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=true&activation_hide=true">link</a>
<hr>
<b>Important:</b> If these don't work first try, play it again. It's completely random.
<h2>Blue and Orange</h2>
In our Neural Network Playground, you'll deal with the very realistic classes of Blue Points and Orange Points.
<br>
The background color is the model's prediction: what color our neural network thinks points in that area are.
<br>
How often the prediction disagrees with the actual color of the points is the loss of the model.
<br>
You can see the loss of your model right above the image, as a graph of loss over time, and as your current loss.
<h2>Neurons: Better Together</h2>
Take a look at what happens when you try using just one neuron to solve the problem.
1. Click <a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=2&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=false&activation_hide=true">here</a> to open a playground with just one neuron. 
<br>
2. Click the Play button to see how one neuron attempts to solve the problem.
<br>
3. Wait for the loss to stop changing and write it down.  You'll compare it with later models as you go.
<br>
A single neuron can only classify points linearly: splitting the data along a single straight line, just like your neuron did.  However, this data isn't linear!  What to do, what to do...
<br>
4. Click here to open a playground with two neurons, or click the + above the neuron to add a second.
<br>
5. Click the play button to run the model.
<br>
6. Write down the loss once it stops changing to determine which did better.
<br>
In this pair, each neuron splits the data linearly, and then the results are combined.  You can mouse over each individual neuron to see how it's splitting the data.  
<br>
7. Try adding a third and fourth neuron with the plus sign above the neurons. 
<br>
8. Re-run the model each time, and write down your loss.
<h2>Solution: Infinite Neurons?</h2>
More neurons seem to do better, so why not just add lots and lots and lots of neurons?
<br>
Well, your playground is capped at <a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=8&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=false&activation_hide=true">eight neurons</a>. Go ahead and try the eight neuron model, and record your loss.
<br>
Try re-running the <a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=1&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=false&activation_hide=true">one</a> and <a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=8&seed=0.65082&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=false&activation_hide=true">eight</a> neuron models and note how long it takes each for the loss to stop changing.
<br>
Because this is a playground and a pretty simple example, both models finish fast, but the eight neuron model is slower.
<br>
While more neurons can reduce a model's loss, as more neurons are added, it takes longer and longer to process all of the information.
<h1>Weights</h1>
Each neuron adds information to the model.  To get a final model, the neural network needs to combine this information into a single result.
<br>
The network uses weights to determine how much influence each neuron should have.  A large weight means that neuron is important and adds a lot of information.  A small weight means that neuron doesn't add as much information but should still be considered.  A negative weight means that the neuron should be inverted (blue becomes orange, orange becomes blue) before being considered.
<br>
Weights are one of the main things the model learns as it runs, changing weights on individual neurons a bit at a time to lower the loss.  The result of each neuron is examined to see how close it was to the correct answer.  If it was correct, the weight is raised; if it is was wrong, the weight is lowered.
<br>
In your playground, the lines running from inputs to neurons and neurons to the result are weights: blue is positive, orange is negative, and thickness is how large the weight is.
<br>
You can click on individual lines to change their weights.
<br>
Try re-running a few models and look at how the weights change as the model is generated.  How does the resulting model change if you modify the weights?
<h1>Layers</h1>
Neural networks are not limited to having neurons in one straight line.  You can create multiple layers of neurons, with each layer feeding information to the next, and the final layer combing the results to produce the overall model.
<br>
Layering neurons can create models that can understand more complex information with less total neurons.  Each layer helps examine the underlying data, making the task of the next layer easier.
<br>
By layering neurons, later layers can examine the results of the work done by earlier layers, rather then all of the neurons examining the underlying data. That way, the model can build up information, processing the data one step at a time.
<br>
A <a href="https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.78878&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false&showTestData_hide=true&stepButton_hide=true&problem_hide=true&noise_hide=true&discretize_hide=true&regularization_hide=true&dataset_hide=true&batchSize_hide=true&learningRate_hide=true&regularizationRate_hide=true&percTrainData_hide=true&numHiddenLayers_hide=false&activation_hide=true">multi-layer model</a> is an effective choice for this dataset.
<h1>Other Databases</h1>
When you're ready, try out some of the other datasets on the left side of the page.
<br>
The goal is to get a low loss with as few neurons as possible. Keep track of your results as you go.
<h1>Recap</h1>
Neural networks are a powerful machine learning method for classifying data.
<br>
By combining the simple classifications of single neurons into a larger model using weights, even very complex datasets can be classified efficiently.
<br>
Real data scientists make notes and compare models by examining the loss of each model.  Because machine learning always has some randomness, models are run multiple times, and the average results are compared.
<ul>
  <li>Classification is the task of separating data into two or more classes</li>
  <li>Loss measures how well a model accomplished this task</li>
  <li>A single neuron can only split data along one line</li>
  <li>Multiple neurons can be combined by weighing their results</li>
  <li>By combining neurons in layers, we can improve a model without adding too many neurons</li>
</ul>
