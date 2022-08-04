<a href="/v4/Text-Generation/Build-a-RNN.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Wrap-Up/Project-Submission.md">Next &gt;</a>
<hr>
<h1>Generating Text</h1>
Now that your model is trained, it's time to actually use it to generate text. Each time you call the model, you give it an "internal state" and some text. The model returns a prediction for the next character and an updated state that you can use to put back into the network to predict.
<h2>Define a One Step Model</h2>
This is what each "step" of the prediction looks like. In order to generate text, you will create a new class that uses the model to predict new text.
1. Define your class
<pre>class OneStep(tf.keras.Model):</pre>
2. Define an initialization function.
<pre>
def __init__(self,model,chars_from_ids,ids_from_chars,temperature=1.0):
super().__init__()
</pre>
3. Set arguments
</pre>
self.temperature = temperature
self.model = model
self.chars_from_ids = chars_from_ids
self.ids_from_chars = ids_from_chars
</pre>
4. Create a mask to prevent "<code>[UNK]</code>" from being generated
<pre>skip_ids = self.ids_from_chars(['[UNK]'])[:,None]</pre>
5. Using a sparse tensor, but a -inf at each bad index, and match the shape to the vocabulary.
<pre>sparse_mask = tf.SparseTensor(values=[-float('inf')]*len(skip_ids),indices=skip_ids,dense_shape=[len(ids_from_chars.get_vocabulary())])</pre>
6. And add the prediction mask to the one step model.
<pre>self.prediction_mask = tf.sparse.to_dense(sparse_mask)</pre>
<img src="https://i.imgur.com/pFeWNDn.png">
<br>
7. Create a function that will generate one step.
<pre>
@tf.function
def generate_one_step(self,inputs,states=None):
</pre>
8. Convert strings to token ids.
<pre>
input_chars = tf.strings.unicode_split(inputs,'UTF-8')
input_ids = self.ids_from_chars(input_chars).to_tensor()
</pre>
9. Run the model.
<pre>predicted_logits,states = self.model(inputs=input_ids,states=states,return_state=True)</pre>
10. Only use the last prediction.
<pre>
predicted_logits = predicted_logits[:,-1,:] 
predicted_logits = predicted_logits/self.temperature
</pre>
11. Apply your prediction mask
<pre>predicted_logits = predicted_logits</pre>
12. Sample the output to generate ids
<pre>
predicted_ids = tf.random.categorical(predicted_logits,num_samples=1)
predicted_ids = tf.squeeze(predicted_ids,axis=-1)
</pre>
13. Convert from ids to characters
<pre>predicted_chars = self.chars_from_ids(predicted_ids)</pre>
14. And return your predicted characters and the model state
<pre>return predicted_chars,states</pre>
15. Create a one step model using this class.
<pre>one_step_model = OneStep(model,chars_from_ids,ids_from_chars)</pre>
<img src="https://i.imgur.com/7g7NUNq.jpg">
<h1>Generate Text</h1>
Now that you have a single step in the form of a model, it's time to use it to generate text. Use the onestep model in a for loop to get a prediction for new characters. All you need is some text to start. 
1. Just to know how long this process takes, get a timestamp.
<pre>start = time.time()</pre>
2. Initialize the states to none.
<pre>states = None</pre>
3. Start the prediction with some text.
<pre>
next_char = tf.constant(['\n\n'])
result = [next_char]
</pre>
4. Use the one step model in a for loop to make predictions.
<pre>
for n in range(1000):
  next_char,states = one_step_model.generate_one_step(next_char,states=states)
  result.append(next_char)
</pre>
5. Take the result and join it together to create a string.
<pre>result = tf.strings.join(result)</pre>
6. Take tne end time stamp
<pre>end = time.time()</pre>
7. And print out your results.
<pre>
print(result[0].numpy().decode('utf-8'),'\n\n'+'_'*80)
print('\nRun time:',end-start)
</pre>
<img src="https://i.imgur.com/Uynp1IC.jpg">
<h1>Improving the Model</h1>
Now that you can use your model to generate text, you know that it works! You might have noticed, that some of the words that the model is generating aren't real words, or that the grammar isn't quite what you wanted.
<br>
This is your chance to improve the model. Can you think of some ways that you could improve the model?
<br>
1. Experiment with the model and see if you can improve it. Below are some ideas for where to start.
<hr>
<b>Epochs:</b> Does training the model for more epochs improve the model.
<br>
<b>Start String:</b> Experiment with the string to start the network and see how that affects the output.
<br>
<b>Add a Layer:</b> Add a RNN layer to improve the models accuracy.
<br>
<b>Adjust Temperature:</b> Adjust the temperature to reduce random predictions.
<hr>
<h2>Save and Export</h2>
Once you are happy with your model, you should export it so that you can reload it and use it to 
<br>
1. Save your model.
<pre>tf.saved_model.save(one_step_model,'one_step')</pre>
2. Reload the model here.
<pre>one_step_reloaded = tf.saved_model.load('one_step')</pre>
3. You can use that reloaded model in place of the model to predict new letters.
<br>
<img src="https://i.imgur.com/MANolr7.jpg">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/y2x58VB.png">
<h1>Recap</h1>
Now that you can create a RNN to generate text, you can see the fruits of your labor. Creating a one step class allows you to do just one step of the network. You can put the one step in a loop and use that to generate text. 
<ul>
  <li>Collect your own text data and use this structure to generate even more text</li>
</ul>
