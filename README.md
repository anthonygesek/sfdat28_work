# Home Brewer's Hop Guide

This project was an attempt at making a recommendation of what ingredients to use when writing a beer recipe to brew at home.  As a home brewer myself, I tended to fly by the seat of my pants a bit when writing a recipe but with this I can give some more direction.

There are three Python Notebooks that explain my process and a set of slides that summarize the whole project. I also uploaded my final data set which is a small subset of the information available at brewerydb.com (the API I used). I am not uploading the entire data set I pulled from them out of respect for what they provide so if you want more beer information than I have here, please check them out.

## Part 1:  Gather, explore, and clean the data

This first step was to find as much information about beers as I could. After searching for the most consolidated set of data on beer, I eventually landed on brewerydb.com as an API. This notebook illustrates how I parsed the JSON file that is provided by breweryDB. I started with the free version and pulled all the beers that had an IBU provided. I then used machine learning to fill in missing values for original gravity, SRM (color), and ABV. I also filled in 72 missing style ID's by hand.

## Part 2: Gather ingredient information 

I decided to pay for a couple months worth of API access to get ingredient information since that was the easiest way to gather that kind of data. Once the account was established I was able to access every beer they have in the database (over 59,000) with ingredients and brewery information. After exploring this new data set I found that it was heavily skewed to American beers so I decided to focus on those alone. The way that I originally parsed the ingredient data was a bit disorganized so I condensed the lengthy feature column list of ingredients I had into one feature column as a list of hop names. I also added ingredient information to beers that had the ingredients listed in their description. I then created new feature columns that were the averages of the characteristics of the hops listed for the beers. 

## Part 3:  Cluster and recommend

After the data set included the basic information about beers and some of the more detailed ingredient information, I grouped them using K-Means clustering which yielded some very helpful information. The clustering ended up being mostly based on a hop profile so I was able create a machine learning model that took in a desired ABV, IBU, gravity, Style, and Color and spat out which cluster that belonged in and the most common hops of that cluster. Thus a hop recommendation for homebrewing was delivered.

## Next Steps: The future!

  * I would like to add malt information to the data set and then potentially regroup the beers once they have that information. 

  * Since this was a project for a class I felt a time crunch so left some of my machine learning models as they were instead of fine-tuning them, so I would like to go back and fine-tune them a bit more.

  * I would also like to finish building my Heroku App to show this information to the public. 

