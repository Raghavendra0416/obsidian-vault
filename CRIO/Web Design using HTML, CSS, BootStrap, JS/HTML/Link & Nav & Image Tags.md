What is Link?
How do we create a link?
What does **href** mean? and how it is used while creating links?
How do we navigate between pages using links?

What is Nav tag?
Is Nav tag and bookmarks same concept? if not how?
What is the relation between Nav tag and link? a real life analogy?
Why do we use Nav tag?

---
### All About Links

1. **What is Link?**
    A link (or "hyperlink") is a clickable piece of text or an image that takes you from one place to another. It's the main way you "browse" the web.

2. **How do we create a link?**
    You create a link using the < a> tag (which stands for "anchor"). The text you want to be clickable goes between the opening <a> and closing </a> tags.
    
3. **What does href mean? and how it is used?**
    href is short for "hypertext reference." It is the most important attribute (a setting) of the       < a> tag. Its job is to tell the browser where to go when the link is clicked.

4. **How do we navigate between pages using links?** Practice. Without Practice navigation will be difficult.
	You put the file name or web address (URL) of the other page into the href attribute. When a user clicks the link, the browser reads the href and loads that new page.
   -  "./" - this represents we are taking about current folder.
   - "../" -  this represents we are before folder.
   - We use these ./ and ../ to navigate between folders. 
   - Example1: If we want to navigate to the file in the same folder we can use ./. Or if we want to navigate from sub folders to main - we have to use ../
   - ./ and ../ is same for images as well.
- Extra Information: 
	- If there are many pages we will see links like Home || Support || About || Other. 
	- Here we use nav tag to put all the links in a single bucket, so we can use CSS to make changes to the all links at a time. 

### All About the `<nav>` Tag

1. **What is Nav tag?**
	The < nav> tag is a container (a box). Its job is to group together the main navigation links for your website (like "Home," "About," and "Contact").
    
2. **Is Nav tag and bookmarks same concept? if not how?**
    No, they are different.
    -> **`< nav >` tag:** This is the **toolbox** (the container).
    -> **Bookmark (`<a href="#section">`):** This is a specific _type_ of **tool** (a link) that makes you          jump to a spot on the _same page_.
	You can put bookmark links _inside_ a `<nav>` box, but they are not the same thing.
    
3. **What is the relation between Nav tag and link? (Real life analogy)**
	This is the "toolbox" analogy from our last chat:
	    -> **The Link (`<a>`) is the tool** (e.g., a hammer, a screwdriver). It does the _action_ (takes             you somewhere).
	    -> **The Nav Tag (`<nav>`) is the toolbox.** It _holds_ the tools.
        -> **Relation:** The `<nav>` tag's main purpose is to hold your most important `<a>` links,           keeping them organized.
        
4. **Why do we use Nav tag?**
    We use it to give our code meaning.
    1. **For Screen Readers:** It helps visually impaired users (who use screen readers) quickly find the "main navigation" on your page.
    2. **For Developers:** It clearly says, "This isn't just _any_ group of links; this is the _main menu_."

### Example (Putting It All Together)


```HTML
<nav>
  <ul>
    <li>
      <a href="about-us.html">About Our Company</a>
    </li>
    
    <li>
      <a href="https://www.google.com">Search Google</a>
    </li>

    <li>
      <a href="#contact-info">Jump to Contact</a>
    </li>

  </ul>
</nav>

<section id="contact-info">
  <h2>Contact Information</h2>
  <p>Our office is at 123 Main Street.</p>
</section>
```

---