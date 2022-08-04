<a href="/v4/Sentiment-Analysis/Final-Touches.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Text-Generation/Building-a-RNN.md">Next &gt;</a>
<hr>
So far you have created two kinds of sequential networks. Both densely connected and convolutional neural networks work by feeding data through a series of layers of neurons.
<br>
Now you are going to learn about an entirely new kind of network called a Relational Neural Network. Instead of simply using the data from a previous layer, these networks take into account the context of the data. This makes them especially good at data that is sequential, like text or video.
<br>
Think about it like this: if you were given a single frame of a ball and told to guess what direction the ball was going, it would be impossible. However, if you were given a video of a ball being thrown through the air, you could use the frames before to figure out where the ball is headed. This is the kind of learning that an RNN does.
<h1>Prepping Text Data</h1>
Like all neural networks, the first phase of this process is all about data preparation. In this instance, you will need to create your own inputs and outputs using a text file. 
<br>
The very first step in this process is to import all the data you need to train the network. For this project, you are going to use recipe text pulled and reformatted from a dataset of recipes. But truly any text data will work, so if you want to try it out with another text file, feel free. 
<br>
1. Inside your student folder, create a new folder for this project. 
<br>
2. Create a new notebook in that folder. 
<br>
3. Download <a href="https://drive.google.com/uc?id=1SuGePtaiSfEA0Exs1ZnjSY89Ie-kP5Qq&export=download">this text file</a> and put it in your project folder. 
<br>
4. In the first code cell, import these libraries:
<pre>
import tensorflow as tf
import numpy as np
import os
import time
</pre>
5. Set the file path in to a variable.
<pre>path_to_file = ('recipes.txt')</pre>
6. Open the file and decode it. 
<pre>text = open(path_to_file,'rb').read().decode(encoding='utf-8')</pre>
7. Look at the first 250 characters in the text. 
<pre>print(text[:250])</pre>
8. Run the cell to see the first 250 characters.
<br>
<img src="https://i.imgur.com/2ANWXxD.png">
<h2>Length and Unique Characters</h2>
Now that you have the data imported, you will need to figure out how long it is and to create a vocabulary from the data. You might have worked with vocabularies in machine learning before, but essentially this will become the list of all possible inputs and outputs for the network to choose. 
<br>
1. Create a new code cell. 
<br>
2. In the cell add this code to see the length of the data.
<pre>print(f'Length of text: {len(text)} characters')</pre>
3. To see how many unique characters are in the data, add this code:
<pre>
vocab = sorted(set(text))
print(f'{len(vocab)} unique characters')
</pre>
<img src="https://i.imgur.com/7XSUPNz.png">
<h1>Vectorizing</h1>
In order to put the text data into your network, you will need to convert letters into numbers. You already have a vocab created that contains all the characters in your training data. In order to understand how the tokenization process will work, follow the instructions below to tokenize some example text.
<br>
1. Create an array with some example strings
<pre>example_texts = ['abcdefg','xyz']</pre>
2. Split the example text into characters.
<pre>chars = tf.strings.unicode_split(example_texts,input_encoding='UTF-8')</pre>
3. Print the chars.
<br>
<img src="https://i.imgur.com/Np0YGy4.png">
<br>
4. Create a function that will convert characters into ids 
<br>
5. Print those ids
<br>
<img src="https://i.imgur.com/zjLE57R.png">
<br>
6. Create another function that will convert the ids back into characters.
<br>
7. Print those ids.
<br>
<img src="https://i.imgur.com/KQ0liVi.png">
<br>
8. Create a function that gets text from the ids using tf.strings.reduce_join.
<pre>
def text_from_ids(ids):
  return tf.strings.reduce_join(chars_from_ids(ids),axis=-1)
</pre>
9. Print the text_from_ids
<pre>print(text_from_ids(ids))</pre>
<img src="https://i.imgur.com/vgCWjyZ.png">
<h1>Creating the Training Data</h1>
Now that you know how to vectorize text, it's time to create the samples for your network.
<br>
Your prediction task for this network is what should the next character be. You will be creating training examples so for each input sequence the goal output will be the input sequence moved over one character. 
<br>
For example, let's say that your training data is a text file containing the text "Hello World! I am a potato."
<br>
Your first task is to split the text into sequences. You will pick a sequence size and then break the data into small chunks. Because of how the input and labels will work for this network, you will want your chunks to be one character larger than the sequence size.
<br>
For example, using the input "Hello World! I am a potato." and the sequence size of 10, your data would be split into chunks of 11 characters. It will look like this.
<h2>Divide Text into Sequences</h2>
Follow the steps below to take your text data and divide it into sequences. 
<br>
1. First, convert all your text into character ids.
<pre>all_ids = ids_from_chars(tf.strings.unicode_split(text,'UTF-8'))</pre>
2. If you print the id Tensor, you should be able to see that the shape matches the original character length.
<pre>print(all_ids)</pre>
<img src="https://i.imgur.com/FqbDhN9.png">
<br>
Now create a dataset of all the ids:
<pre>ids_dataset = tf.data.Dataset.from_tensor_slices(all_ids)</pre>
4. You can see the first 10 characters of the dataset once it's been converted into chars.
<pre>
for ids in ids_dataset.take(10):
  print(chars_from_ids(ids).numpy().decode('utf-8'))
</pre>
<img src="https://i.imgur.com/viOrbLY.png">
<br>
5. Now that you have a dataset, you can decide your sequence length.
<pre>seq_length = 100</pre>
6. And set how many examples you want to run per epoch. You will set this to the length of the text divided by the seq_length (rounded down).
<pre>examples_per_epoch = len(text)//(seq_length+1)</pre>
7. Now, divide the data into sequences.
<pre>sequences = ids_dataset.batch(seq_length+1,drop_remainder=True)</pre>
8. Look at the chars in the first sequence:
<pre>
for seq in sequences.take(1):
  print(chars_from_ids(seq))
</pre>
9. And the text of 5 sequences:
<pre>
for seq in sequences.take(5):
  print(text_from_ids(seq).numpy())
</pre>
<img src="https://i.imgur.com/P6Yo2Hj.png">
<h2>Create Input and Target Pairs</h2>
<br>
Just like with a classification problem, you need input and a label. For your MNIST data, your input was an image and the label was what number the image represented.
<br>
In this case, your input will be the first 100 characters of your sequence, and the label will be the last 100 characters of your sequence. Let's look at our Hello World example to see this in action. 
<br>
If the text you are starting with is "Hello World! I am a potato.", and the sequence size is 10, then the first sequence will be "Hello World". When you split it into an input and a label, the first 10 characters would be the input ("Hello Worl") and the last 10 characters would be the label ("ello World").
<br>
The goal is to get the network to predict that the output is "ello World". Your target output/label, in this case, is "ello World".
<br>
Follow the steps to divide your data into input and target sequences. 
1. Create a function that will split a sequence into input text and target text.
<pre>
def split_input_target(sequence):
  input_text = sequence[:-1]
  target_text = sequence[1:]
  return input_text,target_text
</pre>
2. Test your function by splitting some example text.
<pre>print(split_input_target(list("i love id tech")))</pre>
<img src="https://i.imgur.com/IRmdhaB.png">
<br>
3. Now, create your dataset by applying your function to all the sequences.
<pre>dataset = sequences.map(split_input_target)</pre>
4. Make sure that it worked by looking at an example from the dataset.
<pre>
for input_example, target_example in dataset.take(1): 
  print("Input:",text_from_ids(input_example).numpy())
  print("Target:",text_from_ids(target_example).numpy())
</pre>
<img src="https://i.imgur.com/h63caFe.jpg">
<h2>Final Touches</h2>
Now that your data is split up and ready to go, you will shuffle it is ready to be used. Use Tensorflow's built-in methods to set up the final dataset.
<br>
1. Set a batch size so that the data can be entered into the network in batches.
<pre>BATCH_SIZE = 64</pre>
2. Set a buffer size so that you can shuffle the dataset without using too much memory.
<pre>BUFFER_SIZE = 10000</pre>
3. Now use that to set up your dataset.
<pre>dataset = (dataset .shuffle(BUFFER_SIZE) .batch(BATCH_SIZE,drop_remainder=True) .prefetch(tf.data.experimental.AUTOTUNE))<br>print(dataset)</pre>
Now your dataset is ready to be used to train your network! Move into the next lesson to learn about how to create an RNN for text generation.
<h1>Recap</h1>
In this lesson you took text data and prepared it to go into a RNN. First, you vectorized it (turned it into numbers), then split it into sequences. From these sequences you created input and target text, and put all of that into a dataset. 
<ul>
  <li>Follow along with the next lesson to build your network.</li>
</ul>
