<a href="/v4/Sentiment-Analysis/BeautifulSoup-Intro.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/Making-Websites.md">Next &gt;</a>
<hr>
To know more about HTML see <a href="https://bledy-guides.repl.co/html">this guide</a>.
<hr>
In order to learn how to scrape data, and to have a web page to scrape data from, you are going to build your very own web page. 
<br>
Web pages are generally created using HTML, (hypertext markup language). Web pages also use CSS for beautification and Javascript for any functionality. For this project, you will mostly work in HTML and CSS, since your web page won't need to do anything, just hold data.
<br>
To start, open Notepad++ and create an html file.
<br>
1. Use the Window menu to open Notepad++.
<br>
<img src="https://i.imgur.com/pCkuPDb.png">
<br>
2. In the empty file that appears, add this code to indicate what kind of document it is. 
<pre>&lt;DOCTYPE! html&gt;</pre>
3. Add the basic structure for the html code.
<pre>
&lt;html&gt;
  &lt;head&gt;
  &lt;/head&gt;
  &lt;body&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>
4. Click File and select Save As.
<br>
5. Name the file <code>index.html</code> and put it in your student folder.
<br>
<img src="https://i.imgur.com/RAD6mVf.png">
<h2>Editing the Webpage</h2>
You should see that this new repl has three different files. Each file has a specific purpose. Use the graphic below to learn about what makes up a web page.
<br>
<b>HTML:</b> This file contains code for the content of the webpage that you are creating.
<br>
<b>CSS:</b> Code to change and adapt the style of your webpage.
<h1>Adding Content</h1>
Now that you know the structure of a web page it's time to start adding content to the web page. You are going to do this by editing index.html.
<br>
This file is made up of sets of tags. For example, a paragraph tag is &lt;p&gt;.
<br>
1. In between the html tags, create some space.
<br>
2. Find the body tags and make some space in between them. 
3. Create heading tags to give your page a title.
<pre>&lt;h1&gt;&lt;/h1&gt;
4. In between those tags, type text for the heading of the page.
<br>
<img src="https://i.imgur.com/SXP9E0p.png">
<br>
4. Save your index.html file.
<br>
5. Double-click on the file to see it in the browser.
<br>
<img src="https://i.imgur.com/jYcJHK9.png">
<h2>Text</h2>
Now that your webpage has a heading, it's time to add text content to it. The most commonly used tag for text is &lt;p&gt;. The p stands for paragraph.
<br>
1
1
Below the heading tag add a set of paragraph tags for the content.
<pre>&lt;p&gt;&lt;/p&gt;</pre>
2. Inside those tags type some text that will give the page a description. 
<br>
3. Press Ctrl + S to save the file.
<br>
4. Reload the page to see your changes.
<br>
<img src="https://i.imgur.com/PmWbxic.png">
<h2>Images</h2>
In order to advertise your item for sale, you will want to use a picture. In order to add a picture, you will use the img tag, and a source. 
<br>
1. Go on Google and find an image to represent your product.
<br>
2. Add your image to your student folder. It has to be in the same folder as your index.html file.
<br>
3. Below your website description, add an image tag.
<pre>&lt;img&gt;</pre>
4. In between the angled brackets, add the file path to your image.
<pre>&lt;img src="t-shirt.png"&gt;</pre>
5. Save your file and reload the page.
<br>
<img src="https://i.imgur.com/qLFKmQ6.png">
<br>
6. You might have noticed that the image isn't an appropriate size. To adjust the size of the image, add width=200px to the tag.
<pre>&lt;img src="heeley.png" width=200px&gt;</pre>
7. Save your file and reload the page.
<br>
8. Adjust the width by changing the 200 to different numbers until it is a size that makes sense on your page.
<br>
<img src="https://i.imgur.com/bzzMB3b.png">
<br>
Now your image is an appropriate size, and is a teaser for what you are selling.
<h2>Div</h2>
Another popular tag used when creating web pages is the div tag. These are used to create divisions or sections of content on your page. For example, maybe you want to group the picture and item description together so that they have similar formatting, or draw a border around text somewhere in your webpage.
<br>
You can add ids to these divs so they can be referenced from other files (like the stylesheet). 
<br>
For now, we are going to create a description and put that and the image in a div with an id so that we can apply CSS formatting to it.
<br>
1. Create two div tags for your description. Add an id that is descriptive.
&lt;div id="description"&gt;&lt;/div&gt;</pre>
2. Inside the div tags, add paragraph tags.
<pre>&lt;p&gt;&lt;/p&gt;</pre>
3. Inside the paragraph tags, add a description for the item you are selling.
<br>
<img src="https://i.imgur.com/jxzIO6F.png">
<br>
Surround your image with div tags. You will use this div to help style the page next.
<br>
5. Add an id to the div tags, so that you can reference it later.
<br>
6. Create another set of divs with an id around the image and description.
<br>
<img src="https://i.imgur.com/ofwV5QO.png">
<h1>Styling the Webpage</h1>
Now that you have some content in your page, it's time to start styling it! This is where you get to decide things like font color, backgrounds, font, and move elements around the page. 
<br>
First, let's give the page overall some colors and fonts. CSS files are made up of selectors and declaration blocks. The selector decides which HTML tags to apply the formatting, and the declaration blocks decide what formatting to apply. 
<br>
1. In Notepad++ click File and select New to make a new file.
<br>
2. In the empty file create a selector for the body and a declaration block to contain the formatting.
<pre>
body {<br>  
}
</pre>
3. Inside the curly braces, set the background color.
<pre>background-color: green;</pre>
4. Choose a font color.
<pre>color: burlywood;</pre>
5. Add padding to keep spacing in between the elements.
<pre>padding: 10px;</pre>
<img src="https://i.imgur.com/8uAo9m9.png">
<br>
6. Click File > Save to save your file. Name it "style.css".
<br>
<img src="https://i.imgur.com/5tvunDf.png">
<br>
7. Open your index.html file.
<br>
8. In between the head tags, add this to import your CSS code.
<pre>&lt;link rel="stylesheet" href="style.css"&gt;</pre>
<img src="https://i.imgur.com/aayhYTG.png">
<br>
9. Make sure you save both your files and reload to look at the changes you made.
<br>
<img src="https://i.imgur.com/12zKgiy.png">
<h2>Moving Elements</h2>
Now that you have some color and basic formatting in the document, it's time to make sure that all of the elements are in the right spot. In order to do this with CSS you are going to use float. This detaches the element from its location on the page and allows you to have it relocate either left or right on the page.
<br>
You want the picture to be left and the description on the right. In order to do this, you are going to use the id of the elements you want to float, and the float property.
<br>
1. Add another selector and declaration block to reference the picture.
<pre>
#image {<br>  
}
</pre>
2. Inside the declaration block, use the float property to float the image to the right.
<pre>float: left;</pre>
3. Create another selector and declaration block for the description, and add the code to float it to the right.
<pre>
#description {
  float: right;
}
<pre>
<img src="https://i.imgur.com/m4kzr9f.png">
<h1>Adding Reviews</h1>
So far you have all the basic bare bones of the website. Now it's time to add information for your program to scrape data from.
<br>
1. Create a div with a descriptive id to hold all of the reviews.
<pre>&lt;div id="reviews"&gt;&lt;/div&gt;</pre>
2. Inside the review div, add a paragraph tag with the name of the reviewer.
<pre>&lt;p id="name"&gt;Luke Skywalker&lt;/p&gt;</pre>
3. Underneath the name, add another paragraph to contain the contents of a review.
<pre>&lt;p id="content"&gt;I liked this shirt a lot it is very green and very cool and all my friends recognize me as a jedi&lt;/p&gt;</pre>
4. Repeat this to add as many reviews as you like.
<br>
<img src="https://i.imgur.com/Sffi7Cr.png">
<br>
6. In style.css, create a new selector for the reviews, and a declaration box.
<pre>
#reviews {<br>  
}
</pre>
7. Inside the declaration block, add this code to make sure the reviews display after all the previous content.
<pre>clear: both;</pre>
<img src="https://i.imgur.com/PfEkSac.png">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/son2L3E.png">
<h1>Recap</h1>
A webpage is made up of an HTML file for the content, and a CSS file for style. You can add text and images using HTML tags, and then use CSS to add styles to those elements.
<ul>
  <li>Add more reviews to your webpage.</li>
  <li>Work more on the style of your webpage using CSS.</li>
</ul>
