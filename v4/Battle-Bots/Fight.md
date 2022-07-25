<a href="/v4/Battle-Bots/Other-Abilities.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Battle-Bots/Magic-8Ball.md">Next &gt;</a>
<hr>
<h1>Get Stats</h1>
Now that the robot is complete, display its stats after every turn. Because the fighting happens in the code, you'll need to print what's happening to visualize the action.
<br>
<img src="https://i.imgur.com/MfRFq9p.png">
<h1>Fight!</h1>
Now that you have finished Battle Bot code, it's time to battle a neighbor. Follow these steps to see who the ultimate battle bot winner is.
<br>
1. Paste this code in a new Jupyter NB:
<pre>
class Arena:
    def __init__(self,Bot1,Bot2):
        self.bbot1 = Bot1
        self.bbot2 = Bot2
    def battle(self):
        while self.bbot1.is_alive() and self.bbot2.is_alive():
            # begin battle round
            if self.bbot1.speed &lt;= self.bbot2.speed:
                self.bbot1.action(self.bbot2)
                self.bbot2.action(self.bbot1)
                self.bbot1.get_stats()
                self.bbot2.get_stats()
                input("Press enter for next round")
            else:
                self.bbot2.action(self.bbot1)
                self.bbot1.action(self.bbot2)
                self.bbot1.get_stats()
                self.bbot2.get_stats()
                input("Press enter for next round")
        if self.bbot1.is_alive():
            print(self.bbot1.name+" is the winner!")
        else:
            print(self.bbot2.name+" is the winner!")
</pre>
2. Now paste your robot's code below the Arena Code.
<br>
3. Below your robot's code, paste other person's robot code.
<br>
4. Finally, put this code at the end of the NB, and put the class name of the robots in the "bot1" and "bot2" areas.
<pre>
Bot1 = # your robot's class name here
Bot2 = # other person's robot class name here
arena = Arena(Bot1,Bot2)
arena.battle()
</pre>
Here's what your project could look like at this point. The finished code is an example of how it might've turned out. Your code might have different probabilities for different actions.
<br>
<img src="https://i.imgur.com/GY6OjWP.png">
<h1>Recap</h1>
Now you have built a battle bot with the ability to do different things depending on a randomly generated number.
<ul>
  <li>Battle a neighbors bot!</li>
  <li>Add more functions or adjust the probability of different actions happening.</li>
</ul>
