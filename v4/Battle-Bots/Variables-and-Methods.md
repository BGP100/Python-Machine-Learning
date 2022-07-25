<a href="/v4/Functions-and-Classes/Making-a-Class.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Battle-Bots/Variables-and-Methods.md">Next &gt;</a>
<hr>
The battle bots competition is about to begin! You'll create a robot with a unique skill set to bring into the ring.
<br>
<b>What will your robot do?</b>
<br>
What type of attributes should your robot have? What type of actions will it take?
<br>
In this project, you'll be creating unique battle bots using classes. Afterward, let them battle it out in an arena! Follow these steps to start your Battle Bot class.
<br>
1. In your notebook, create a BattleBot class.
<br>
2. Add two parameters: self and name.
<br>
<img src="https://i.imgur.com/AcqHuwO.png">
<br>
The Robot's Characteristics  
When creating a robot, what do you need to consider? Like any other object, it needs descriptors and actions. 
<br>
Your battle bot will have these core stats:
<ul>
  <li>Attack</li>
  <li>Defense</li>
  <li>Speed</li>
</ul>
Each stat will be 10 points. These values can change later on, but for now, these values represent how much damage your robot takes and how much damage it can deal.
<br>
Declare these values in the <code>__init__</code> method. These are the robot's starting class properties.
<br>
1. Begin by declaring the <code>__init__</code> method.
Create the variables that define your robot in the <code>__init__</code> method:
<br>
2. Set <code>self.health</code> to 100.0.
<br>
3. Set <code>self.base_armor</code> to 10.0.
<br>
4. Set <code>self.base_damage</code> to 10.0.
<br>
5. Set <code>self.speed</code> to 10.0.
<br>
6. Set <code>self.name</code> to be the value you pass in.
<br>
<img src="https://i.imgur.com/5dq0gVm.png"
<br>
You've just created your robot by defining its properties. Now bring it to life by programming what it can do.
<h1>Abilities</h1>
The variables you've just defined will be the basis for what the robot can do.
<br>
Your robot will be able to:
<ul>
  <li>Attack</li>
  <li>Build Armor</li>
  <li>Build Attack</li>
  <li>Build Speed</li>
</ul>
<h2>Attack</h2>
Your battle bot must be able to attack in order to fight other bots. When an attack is made, two things happen.
<ul>
  <li>A bot executes the attack</li>
  <li>Another bot takes damage</li>
</ul>
For the attacking bot, nothing changes. However for the defending bot, its health is decreased. To damage the defending robot’s armor, you must pass it as a parameter.
<br>
1. To begin the attack method, declare a function called "attack" that takes self and opponent as an input.
<br>
<img src="https://i.imgur.com/8IjQ8NW.jpg">
<h2>Take Damage</h2>
The next method you need is the  take_damage  method. The objective of this method is to subtract damage dealt from a robot's current health.
<br>
<code>take_damage</code> takes two parameters:  self  and  damage dealt .
<br>
You need  self  to refer to the robot's health using dot notation:  self.health . Once the health is found, you'll subtract the  damage_dealt  from  self.health . 
2. Create a new method called  take_damage  that takes in  self  and  damage_dealt  as parameters.
<br>
3. Inside take_damage, decrease self.health by damage_dealt.
<br>
<img src="https://i.imgur.com/9WJefcL.png">
<h1>Attacking Another Robot</h1>
You'll need a formula to calculate the damage dealt:
<pre>damage_dealt = robotBaseDamage - (robotBaseDamage * opponentBaseArmor / 100)</pre>
This formula will make the damage dealt proportional to the armor of the opponent. But some parts are missing!
<br>
The opponent robot needs to then take damage. You can call the existing  take_damage  method and pass in  damage_dealt .
<br>
1. Call the Opponent's  take_damage  method using dot notation.
<br>
2. Pass in  damage_dealt  as the parameters.
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/oMBhCPH.png">
<h1>Recap</h1>
A battle bot uses the self keyword to refer to itself and change the stats for itself. Methods can take in the opponent battle bot, and use dot-notation to modify an opponents stats.
