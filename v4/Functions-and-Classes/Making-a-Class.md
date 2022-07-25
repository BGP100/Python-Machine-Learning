<a href="/v4/Functions-and-Classes/Functions.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Functions-and-Classes/Inheritance.md">Next &gt;</a>
<hr>
Imagine a car. How would you describe your car? Cars have a color, wheels, and a price. Cars can also accelerate, stop, and play the radio.
<br>
A car object is split into two main categories: adjectives to describe it and verbs to represent actions.
<h1>Classes</h1>
Although all cars have these attributes—a color, a number of wheels, and a price—the values of these attributes can be anything. 
<br>
If you were to write code representing five cars, you'll be writing the same code over and over again specifying the details of each car. For example, you'll need five variables for "color" to represent the different colors of each cars.
<br>
This can be tedious, confusing, and messy. OOP allows you to avoid this using classes instead.
<br>
A car class is the blueprint to create cars. It'll have color, wheels, and price, as well as ways to accelerate, stop, and play radio.
<br>
The class has all the variables and functions that are given values when a car object is made. Each time a new object is made, a new instance of a class is made with the values of that object.
<br>
For example, the car class has attributes <b>color</b>, <b>wheels</b>, and <b>price</b>. These variables have no values. 
<br>
But when a new car object is made, these variables are set and can be all be accessed in this one object.
<hr>
<pre>
color = "red" 
wheels = 3 
price = 50000
</pre>
<img src="https://i.imgur.com/1djjuIz.png" width="20%">
<pre>
color = "blue" 
wheels = 8 
price = 10000
</pre>
<img src="https://i.imgur.com/Ka6SsrE.jpg" width="20%">
<pre>
color = "pink" 
wheels = 4 
price = 2000000
</pre>
<img src="https://i.imgur.com/1wFpQ43.jpg" width="20%">
<hr>
<h1>Additional Benefits</h1>
OOP makes code easier to read. It also makes it easier for programmers to work together.
If you're programming a photo booth system, it could be a different programmer's job to create each of the following:
<ul>
  <li>Camera</li>
  <li>Microphone</li>
  <li>Picture viewing screen</li>
  <li>Costume pieces</li>
</ul>
You can then use those same objects in a different program. If someone makes a circus program and wants to take pictures using costumes, they can reuse the objects for pictures and costumes in this new project.
<h1>Writing the Code</h1>
Classes allow you to create reusable objects.
<br>
Create a class by typing:
<pre>class ClassName:</pre>
You'll be making a class for a pet.
<br>
1. At the top of a new file, type:
<pre>class MyPet:</pre>
This is the class declaration.
<br>
2. Don't include the program base for this project.
<br>
3. Save the file. Name it "MyPet".
<h1>Python's <code>__init__</code> Function</h1>
When you create a new pet from the <b>MyPet</b> class, anything in the <code>__init__</code> function will happen first.
<br>
4. Add an init method, also known as the constructor method.
<pre>
class MyPet:<br>
  def __init__(self):
    pass
</pre>
Back in the car example, the color can be red or blue. The color is unique to each object, making these values instance variables.
<br>
The self keyword is used to indicate that functions will be run on a specific object.
<br>
Add a self keyword:
<pre>
class MyPet: 
  def __init__(self,pet_name): 
    self.name = pet_name
</pre>
5. Add a <b>self</b> keyword:
<pre>
class MyPet: 
  def __init__(self,pet_name): 
    self.name = pet_name
</pre>
<h1>Creating Pet Objects</h1>
1. Create a new pet object below your other code, indented evenly with class <b>MyPet</b>, type:
<pre>
orange_cat = MyPet("Miles") 
small_dog = MyPet("Fido")
</pre>
<hr>
<pre>
class MyPet:<br>
    def __init__(self, pet_name):
        self.name = pet_name<br>
orange_cat = MyPet("Miles")
small_dog = MyPet("Fido")
</pre>
You've just created two new <b>MyPet</b> objects, one called <b>orange_cat</b> and one called <b>small_dog</b>!
<br>
2. Try printing out their names using dot notation:
<pre>print(orange_cat.name)</pre>
<h2>Creating Class Functions</h2>
You've created the adjectives describing your pet using variables; now give them the ability to perform actions with functions.
<br>
You'll be adding functions to your class; every pet you make based on that class will have access to those functions.
<br>
1. Inside the  MyPet  class, add a function called  play_fetch(self) : .
<br>
2. Have it print out <code>"Your pet " + self.name + " seemed to be happy to play fetch!"</code>. Now any pet you made can play fetch, and it will use their name.
<br>
3. Call the <code>play_fetch()</code> function on both of your pets by calling your pet name and using dot notation: <code>small_dog.play_fetch()</code>.
<pre>
class MyPet:<br>
    def __init__(self,pet_name):
        self.name = pet_name<br>
    def play_fetch(self):
        print("Your pet "+self.name+" seemed to be happy to play fetch!")<br>
orange_cat = MyPet("Miles")
small_dog = MyPet("Fido")<br>
print(orange_cat.name)
small_dog.play_fetch()
</pre>
<h1>Extra Functions</h1>
Now that you know how to write functions, it's time to see what other stuff you can do with them. What if your pet was able to be pet? What about if the pet made noise? Use these checkboxes to add functions that have that functionality. 
<ul>
  <li>Following the same format as the play_fetch function, create a pet function that prints out the message [pet name] " seems happy that you pet them"</li>
  <li>Create a function called make_noise that prints out "noise, noise, noise".</li>
</ul>
<img src="https://i.imgur.com/wSihxn6.png">
<h1>Recap</h1>
Use the class keyword to make a new class: class NewClass:
<br>
<code>def __init__(self)</code>: is the first function to go in any class, and it's run when you create an instance of that class.
<br>
Call object's functions using dot notation: <code>small_dog.pet()</code>
