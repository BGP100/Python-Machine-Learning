<a href="/v4/Battle-Bots/Variables-and-Methods.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Battle-Bots/Fight.md">Next &gt;</a>
<hr>
<h1>Three Other Abilities</h1>
You'll be rigging your robot with three additional abilities that are similar in structure to each other.
<br>
For example, if a robot wanted to build its attack, then it would lose one point in the other stats and gain two points in attack.
<h2>Build Attack</h2>
Now you can make a method that builds your bots attack. Follow the steps below to write the build attack method.
<br>
1. Make another method called <code>build_attack</code> that takes one input: <code>self</code>.
<br>
2. Reduce <code>self.base_armor</code> by 1.
<br>
3. Reduce <code>self.speed</code> by 1.
<br>
4. Increase <code>self.base_damage</code> by 2.
<br>
<img src="https://i.imgur.com/pYKcBNo.png">
<h2>Is Alive?</h2>
Checking if a robot is alive is important for the robot and the match.
<br>
If a robot never dies, then it will never lose and the battle will go on forever. To check if a 'bot is alive, you'll create a class method called "is alive."
<br>
1. Create a new method called is_alive.
<pre>
def is_alive(self):
  if self.health &lt;= 0:
    return False
  else:
    return True
</pre>
<h2>Where's the third ability?</h2>
I dont know why it says "three more abilities" because there are just two of them.
