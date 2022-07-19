<a href="/v3/ML-Intro/Playable-RPS-Challenge.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Connected-Networks/Machine-Learning.md">Next &gt;</a>
<hr>
Most programming you've done requires you to specify exactly how to complete a task line by line. Machine learning refers to programming techniques that use statistics to allow the program to "learn" and improve at its task.
<br>
This is accomplished by building a model with several adjustable parameters that can attempt to accomplish a task. The model learns by testing repeatedly on the task, then optimizing the parameters toward the expected result. Over time, the approximation made by the model will get closer and closer to the actual expected value!
<br>
<img src="https://i.imgur.com/DBbXbBF.png">
<h1>Types of Tasks</h1>
Machine learning problems can be broken down into a few categories. The main one we'll cover in this course is supervised learning. Supervised learning refers to tasks that have a metric for success, whether it's labeled data or rewards for performing well at the task.
<br>
On the other side, unsupervised learning refers to problems where the model has no guidance and must infer patterns and features in the data independently.
<br>
<img src="https://i.imgur.com/DE22swW.jpg">
<br>
Some of the most frequent problems tackled with supervised learning are Classification problems. In these problems, the model must classify some input data. This can be anything from filtering spam to determining if an image is a picture of a cat or a horse.
<br>
<img src="https://i.imgur.com/L71xTW0.png">
<br>
<b>How Does a Model "Learn"?</b>
<br>
The statistical techniques to perform machine learning tasks have existed for decades, but only recently has the computing power necessary to make it practical become available.
<ol>
  <li>Data is fed into the model. The parameters inside the model take that data and return an answer.</li>
  <li>The model's guess is then compared with the expected outcome. (Was the image a cat or a horse? Did the ghost eat Ms. Pac Man?)</li>
  <li>The parameters are optimized in the direction of the expected outcome.</li>
</ol>
This process is repeated with new data until the model has optimized its parameters to be as likely as possible to guess the right answer.
<h1>What's in a Model?</h1>
We've talked about parameters inside the model, but what exactly does that mean?
<br>
A machine learning model can be as simple as a single variable that changes over time to a whole network of thousands of neurons estimating complex processes. The more parameters a model has, the more nuanced the task it can learn becomes.
<br>
Tuning your machine learning models is a matter of balancing complexity, processing time, and model structure to be the best at learning its task.
<br>
We'll cover how to set up these models and what's inside them in the coming lessons!
<h1>Recap</h1>
<ul>
  <li>Machine learning allows computers to learn and improve at a given task with practice over time.</li>
  <li>Supervised learning refers to machine learning problems where the expected outcome is known and used to train the network.</li>
</ul>
