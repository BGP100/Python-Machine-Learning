<a href="/v4/CIFAR-Data/Test-Your-CIFAR-Network.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/Making-Websites.md">Next &gt;</a>
<hr>
To know more about HTML see <a href="https://bledy-guides.repl.co/html">this guide</a>.
<hr>
Beautiful Soup is a python library created to parse HTML documents. Essentially, it is used to dissect a webpage to find whatever important data a user might want. 
<br>
For this project, you are going to use it to scrape data from a Wikipedia page and do some calculations with it. 
<br>
1. Create a new Jupyter Notebook.
<br>
2. Import beautiful soup and requests.
<pre>
import requests
from bs4 import BeautifulSoup
</pre>
<img src="https://i.imgur.com/EDNKWv3.png">
<br>
3. Open  Wikipedia and find a Wikipedia page that you want to examine. It will work best if you choose one with a lot of content in it.
<br>
4. Select the link at the top of your browser and press Ctl+C to copy it. 
<br>
5. In your notebook, create a variable called URL and set it equal to the link in single-quotes
<pre>URL = "https://en.wikipedia.org/wiki/Piracy"</pre>
6. Import the page using the requests library.
<pre>page = requests.get(URL)</pre>
7. Create a soup object in order to use the Beautiful Soup library.
<pre>soup = BeautifulSoup(page.content,'html.parser')</pre>
8. Run the cell.
<br>
<img src="https://i.imgur.com/Ba2xB8Z.png">
<h1>Inspecting a Page</h1>
Now that you have all the data imported, it's time to start actually getting data from the page. Since you don't actually know what the HTML code of this website is, you will first have to use your browser's built-in tools to get an idea of what you are looking for.
<br>
1. Right-click on a section of the text.
<br>
2. Select Inspect.
<br>
<img src="https://i.imgur.com/E7WXJbV.jpg">
<br>
Now you can see the source code for the page. The highlighted section is the code that represents whatever section you right-clicked on. 
<br>
Looking at this sidebar, you may have noticed the HTML tags. These are surrounded by angled brackets (&lt;&gt;) and help keep track of what kind of information is in each section. These tags come in sets of two, with an opening tag (&lt;tag&gt;) and a closing tag (&lt;/tag&gt;). You can think of these as code to draw a box around the content they surround. Everything in between a tag set can be referenced using that tag. You can use the grey triangles to expand different tag sets.
<br>
Use these flashcards to learn a little more about what some of the tags mean.
<h1>Scraping Data</h1>
Now that you understand some of the tags that are present in an HTML page, you can use those tags in Beautiful Soup to scoop up data from the page into your python program.
<br>
Beautiful Soup uses different functions to help decide what it should take from the webpage. In order to find all the content based on a certain filter, you will use soup.find_all().
<br>
1. In your notebook, create a variable called content.
<pre>content = </pre>
2. Set content equal to all of the paragraph elements from your page.
<pre>content = soup.find_all("p")</pre>
<img src="https://i.imgur.com/TsItWfP.png">
<br>
The content has been pulled, but it is in a massive list. In order to see each individual element, you will need to loop through the list and print out the element. 
<br>
3. Loop through the content.
<pre>for i in content:</pre>
4. Get the text for each element.
<pre>  text = i.get_text()</pre>
5. Use Beautiful Soup's strip function to get rid of extra text.
<pre>  text = text.strip()</pre>
6. Print the text.
<pre>  print(text)</pre>
7. Run the cell.
<br>
<img src="https://i.imgur.com/ZIN9wUZ.jpg">
<h1>Using Classes</h1>
Remember the classes that can be used in div elements? Those can also be used to pull specific data from an HTML page.
<br>
Look at this div tag representing one of the headings in the pirate Wikipedia page.
<br>
<img src="https://i.imgur.com/1QI8mhN.png">
<br>
Look for the part that says <code>class="mw-headline"</code>. This is the class that is used for all of the headings on this page. You can use this class inside the find_all function to find all the headings on this page.
<br>
1. Make a new code cell in your Notebook. 
<br>
2. Create a headings variable that equals all the headings.
<pre>headings = soup.find_all(class_="mw-headline")</pre>
3. Loop through the headings like you did for the content, and print the stripped text.
<pre>
for i in headings: 
  text = i.get_text().strip()
  print(text)
</pre>
4. Run the cell.
<br>
<img src="https://i.imgur.com/1rLMWDA.png">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/QRuOrZs.jpg">
<h1>Recap</h1>
Beautiful Soup is a python library that can be used to collect data from a webpage. You can use HTML tags or classes to decide what data to pull. Once you collect that data you can loop through it and remove extra information to see the final product.  
<ul>
  <li>Follow the next lesson for some challenges based on the information you have scraped.</li>
</ul>
