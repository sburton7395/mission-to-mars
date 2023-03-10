# Mission To Mars - Module 11 Challenge
<sub>Chapel Hill - Data Science Bootcamp</sub>

## Overview of Project
For Module 11, Splinter and Beautiful Soup were used in conjuction with Python, Pandas, and NumPy in Jupyter Notebook to scrape web data from NASA and Amazon Web Services. 

## Method & Results
### Part 1 - Scraping article titles and blurbs from the [NASA Mars news nite](https://redplanetscience.com/)

<details>
<summary>Using Splinter, the automated browser was commanded to connect to NASA's Mars news site, [redplanetscience.com](https://redplanetscience.com/). The home page contains an overview of the most recent articles, with images, titles, and previews. <sub>Click the arrow to show an image of the site at the time of writing.</sub></summary>

![Site at time of writing](images/redplanetscience_siteview.png)

</details>

<details>
<summary>Beautiful Soup took the HTML of [redplanetscience.com](https://redplanetscience.com/), storing all of it in an object. Looking at the raw HTML, we can see which containers hold the desired data. <sub>Click the arrow to show a snippet of the soup object.</sub></summary>

![Site HTML](images/redplanetscience_htmlview.png)

</details>

<details>
<summary>Beautiful Soup's `find_all` function was used to find all areas of HTML contained within a <div class="col-md-8" /> tag. All articles on the website are held within these tags, and each article contains a list date, title, and blurb. <sub>Click the arrow to show a snippet of the extracted article data.</sub></summary>

![Article HTML](images/redplanetscience_articlehtml.png)

</details>

<details>
<summary>Using Python and Beautiful Soup's `find` and `text` functions, the articles' titles and previews were extracted from the HTML and added to a list of dictionaries, with each dictionary containing one article title and blurb. The scraped data was then exported to JSON format ([articles.json](resources/articles.json)) and a MongoDB database. <sub>Click the arrow to show a snippet of the list of dictionaries.</sub></summary>

![Article list](images/redplanetscience_articlelist.png)

</details>


### Part 2 - Scraping and analyzing weather data from the [Mars temperature data site](https://data-class-mars-challenge.s3.amazonaws.com/Mars/index.html)

<details>
<summary>As in part 1, Splinter was directed to connect to the Amazon Web Services [Mars temperature data site](https://data-class-mars-challenge.s3.amazonaws.com/Mars/index.html). The page contains a large table with data on Mars sent from the Mars Rover. <sub>Click the arrow to show an image of the site at the time of writing.</sub></summary>

![Site at time of writing](images/amazonaws_siteview.png)

</details>

<details>
<summary>Using Beautiful Soup, the HTML of the [Mars temperature data site](https://data-class-mars-challenge.s3.amazonaws.com/Mars/index.html) was scraped and sent to an object. <sub>Click the arrow to show a snippet of the soup object.</sub></summary>

![Site HTML](images/amazonaws_htmlview.png)

</details>

<details>
<summary>The Beautiful Soup's `find_all` function extracted all HTML contained in `<tr class="data-row" />` tags. Each individual row in the table is held in one of these tags and contains seven values - the ID number, date on Earth, number of elapsed Martian days since Curiosity landed, solar longitude, Martian month, minimum temperature (°C) of the Martian day, and atmospheric pressure. <sub>Click the arrow to show a snippet of the extracted table rows.</sub></summary>

![Table HTML](images/amazonaws_tablehtml.png)

</details>

<details>
<summary>The Beautiful Soup `find_all` and `text` functions were then used to extract the data from the HTML and send it to a list of dictionaries, with each dictionary containing the values from one row. <sub>Click the arrow to show a snippet of the list of dictionaries.</sub></summary>

![Table list](images/amazonaws_tablelist.png)

</details>

<details>
<summary>This was then translated into a Pandas dataframe. To prepare for data analysis, the data types were also updated (i.e. setting the ID column to integers). <sub>Click the arrow to show a snippet of the dataframe and updated data types.</sub></summary>

![Table dataframe](images/amazonaws_tabledf.png) ![Table data types](images/amazonaws_tabledftypes.png)

</details>

Five questions were answered using the created dataframe:
<sub>NOTE: Click the arrows to show images supporting each answer</sub>
1. How many months exist on Mars?
    <details>
    <summary>A Martian year consists of 12 months.</summary>

    ![Question 1](images/amazonaws_analysis1.png)

    </details>

2. How many Martian days' worth of data exist in the scraped dataset?
    <details>
    <summary>The dataset contains 1,867 unique Martian days.</summary>

    ![Question 2](images/amazonaws_analysis2.png)

    </details>

3. What are the coldest and warmest months on Mars (at the location of Curiosity)?
    <details>
    <summary>Based on the averages created by the dataset, the third month is the coldest and the eighth month is the warmest.</summary>

    ![Question 3 calculations](images/amazonaws_analysis3_1.png) ![Question 3 visualization](images/amazonaws_analysis3_2.png)

    </details>

4. Which months have the lowest and highest atmospheric pressure on Mars?
    <details>
    <summary>Based on the averages created by the dataset, the sixth month has the lowest pressure and the ninth month has the highest.</summary>

    ![Question 4 calculations](images/amazonaws_analysis4_1.png) ![Question 4 visualization](images/amazonaws_analysis4_2.png)

    </details>

5. About how many terrestrial days exist in a Martian year?
    <details>
    <summary>A Martian year is roughly 687 terrestrial days.</summary>

    ![Question 5 dataframe](images/amazonaws_analysis5_1.png) ![Question 5 calculations](images/amazonaws_analysis5_2.png)

    </details>
