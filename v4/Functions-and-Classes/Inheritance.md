<a href="/v4/Functions-and-Classes/Making-a-Class.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Functions-and-Classes/Programs.md">Next &gt;</a>
<hr>
<h1>Class Inheritance</h1>
A dog class could inherit from your pet class. You'd want all the functionalities of the pet class, but with additional code specific to dogs.
<br>
1. In the same file your pet class was created, below all your other code, add a new cell and type:
<pre>class MyDog(MyPet):</pre>
That class will have all the same functions as your MyPet class.
<br>
2. Add a new function in your <b>MyDog</b> class called "bark" that prints out the dog barking:
<pre>
def bark(self): 
  print("Woof woof woof")
</pre>
<hr>
<pre>
class MyPet:
    def __init__(self,name):
        self.name = name<br>
    def pet(self):
        print("Your pet "+self.name+" seemed happy that you pet them.")<br>
    def make_noise(self):
        print("Noise noise noise.")<br>
orange_cat = MyPet("Miles")
small_dog = MyPet("Fido")<br>
print(orange_cat.name)
small_dog.pet()<br>
class MyDog(MyPet):
    def bark(self):
        print("Woof woof woof")
</pre>
<h2>Accessing Base Functions</h2>
3. Make a new dog, and call the pet function from <b>MyDog</b> and the bark function from:
<pre>
my_dog = MyDog("Spike")
my_dog.bark()
my_dog.pet()
</pre>
<h1>Overriding Base Class Elements</h1>
You may decide that your <b>dog</b> class needs extra attributes, different than the <code>__init__</code> function in your <b>pet</b> class. If so, you can override the base class.
<br>
1. Above the  bark  function in  MyDog , add:
<pre>
def __init__(self, name, volume): 
  self.name = name 
  self.volume = volume
</pre>
2. Then in your bark function, add:
<pre>
if self.volume &gt; 3: 
  print("Woof woof woof") 
else: 
  print("Yip yip yip")
</pre>
<hr>
<pre>
class MyDog(MyPet):
    def __init__(self,name,volume):
        self.name = name
        self.volume = volume<br>
    def bark(self):
        if self.volume &gt; 3:
            print("Woof woof woof")
        elif self.volume &lt; 3:
            print("Yip yip yip")<br>
small_dog = MyDog("Pup",2)
big_dog = MyDog("Coco",5)<br>
small_dog.bark()
big_dog.bark()
</pre>
<h1>Program Order: Creating a Game</h1>
Create a main game file to add logic and structure, similar to your program base. 
<br>
This main file will contain the code to your program that will utilize the classes you create.
<br>
1. Create a new module and save it as "PetGame".
<br>
2. Add the following to it:
<pre>import pygame<br>class PetGame:</pre>
The classes that are imported keep things organized.
<br>
1. Below <code>class PetGame:</code>, add:
<pre>
def main():
  a_dog = MyDog("Rover",6)
  a_dog.bark()
</pre>
2. Then add:
<pre>
if __name__ == "__main__": 
  main()
</pre>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/hoevErE.png">
<h1>Recap</h1>
To import classes use: <code>from FileName import ClassName</code>.
<br>
Parentheses after the class name indicate you want to inherit from another class:
<br>
<code>class MyClass(InheritedClass):</code>
<br>
You can use all the values and functions from the class you inherit from.
