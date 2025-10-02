# Interview with a Wildfire PIO and Volunteer Firefighter, Redding, California
**Date**: November 24, 2024  
**Context**: I conducted this interview on November 24, 2024, with a Redding, California, Public Information Officer (PIO) and volunteer firefighter to inform feature selection for Omdena’s AI-Powered Forest Fire Prediction and Early Warning System for Uttarakhand. It provided critical insights into wildfire behavior, containment strategies, and data needs, shaping the design of a machine learning-based prediction tool. [See my project repository](https://github.com/ashleysally00/Uttarakhand-Land-Surface-Temperature-LST-Analysis-Using-GEE).

## Overview
This interview aimed to identify data critical for predicting wildfire spread, drawing on the practical experience of a PIO and volunteer firefighter involved in multiple California wildfires. The findings guided feature engineering for the Omdena project’s AI tool.

## Interview Content
### Wildfire Experiences
**Question**: What fires were you involved in?  
**Answer**: I worked on: August Complex Fire (2020), Hirz Fire (2018), McFarland and Monument Fires (2021), South Fire (2019).  
- The Carr Fire (2018) was notable, as I evacuated my house. It burned downhill unusually, created a fire tornado, and reached Redding, stopped by the Sacramento River and I-5. Firefighters had to secure all flanks to prevent re-ignition a month later.

### Containment Strategies
- **Firelines and Backburning**: Firelines are ineffective in high winds (e.g., 40 mph). Backburning creates a burned zone to stop fire spread by consuming fuel.  
- **Goal**: Contain, not extinguish, fires by managing fuel and terrain.

### Data Needs for Machine Learning
- **Key Data**: Satellite-based infrared data for fire spread rate, topography (slope, aspect), fuel type, and weather (wind, inversion layers).  
- **Application**: Machine learning can correlate these factors to predict fire spread and optimize fireline placement, ensuring firelines are built close enough to the fire but safely timed.

### Implications for AI Tool
The interview highlighted the need for features like fire spread rate, fuel conditions, and terrain analysis, ensuring the tool’s practical utility for firefighters.

[Note: One sentence about fireline distance (“You can't put the fireline about 20 feet in front of the fire”) is pending fact-checking with the interviewee.]

------------------------------------------------------------------

**What fires were you involved in?** I worked on: August Complex Fire (2020), Hirz Fire (2018), McFarland and Monument Fires(2021), South Fire(2019).

We evacuated our house in the Carr Fire (2018): it marinated for a week and then created a tornado of fire, and we evacuated our house. The fire burned downhill which is unusual, we don’t know why, it should not have done that, it burnt downhill and at night into Redding. We had the Sacramento River and I-5 and that stopped its forward motion finally. The firefighters had to go in and make sure it was contained on all of the flanks or a month later another windstorm would kick it back up. 

Nothing can contain that 300 mph or 70 mph wind that went through Redding. But you needed to contain it in the 5 days before it got to Redding. The Parks Service wasn’t putting it out as fast as they should have because they thought the burning would be good. It probably didn’t occur to them that the fire could burn up like it did. It was 2018. They had the Hirz the Carr Fire the Delta Fire and the Camp Fire. It was a crazy year for fire, and we do not quite know why. Why was 2018 a crazy fire year in Northern California?

But the Tubbs Fire and Thomas Fire (Los Angeles) and the Thomas Fire was on Christmas Day. They had not had rain all year. They were trying to figure out if there would be mudslides. They had predicted for landslides after the fire was done so they could tell people if they needed to evacuate or not after the fire.

They wanted people to be able to be prepared for when the landslides came after the fire since the vegetation was gone, which causes landslides. 100-year worst case scenario, they said these areas would be okay, but it was not. So, there was a 1000-year event (a one in one thousand risk that the rain would fall in a certain quantity), so, they would say there is a less than 1 in one thousand chance of it occurring.  

Some of the areas where they told people where it would be safe, it was not. Maybe the models for predicting rain were wrong. The problem was that they based their model on a predicted amount of rain. They got the highest amount of rain that you could possibly get over a 1000-year period. Maybe they were wrong.

There were those years where fires were insane, and we do not know why, like in 2017 (Coast of California burned), 2018 (Northern and Central Valley, Redding, Chico), 2021(Sierras: Dixie Fire). It is probably a combination of long-term weather patterns, long term fuel conditions, which then depend on the weather patterns over the past 100 years. Also, humans can be good at finding patterns where they do not exist. But it seems to me more than a coincidence that we had all these fires all in one year, all within 100 miles of each other. Including the Coastal Fires. 

## Prediction, Containment and Firelines

Prediction is useful because it tells you where to build the fireline. Firelines do not work when there are 40 mph winds. They just don’t. You have to get it contained before then. When the wind is so high, it can go over the fireline, the fireline is not going to stop it. But if the flank is secure, the 40 mph wind won’t matter, by then the fire is not burning so much it will not jump it. There is not fuel there. You have burned the fuel away first. That is what containment means. Containment means that there is so much of a zone where the fire cannot burn. And the outside of that zone is the fireline itself.

Just as important to containment is inside the zone, where it is contained enough, it might not still be burning, it might be burning a little, but it is not burning a lot. 
If we put the firelines in 100 miles ahead of the fire, it does not help. The wind will push the fire over the fireline.

If we had a better idea of how it was behaving, we could put our firelines in at the right place. You could also evacuate communities better because you would know where the fire 
Understand that what you are trying to do to put out a fire is to remove all the vegetation on the surface of the ground. It will not work if the fire is burning at the tops of the trees. Ideally you want the fire to burn up to the fireline, where it is burning hot enough to consume the material but not so hot as to be able to jump the fire line. But it is hard to do that because it is usually a brute force thing where you hope that the fire hits the fireline at the right time. 

You know the cycles. There is also backburning, where you’ve got a fire line, the fire is burning but it is not burning so crazy, you put the fire line on a ridge, which is the best place to do it. You clear eight feet wide with a bulldozer. You need to be far enough ahead so that you do not get burned up. If the fire gets enough momentum going up the hill, it may jump the fire line at the top. So, we go in at night and do a backburn. 

## Containing the Fire with Backburn

A backburn is where you light the forest from the fireline and allow the fire that you lit to burn into the fire that was already burning. You might go in at 11 at night or 2 or 3 in the morning. You light the fire with your torch and try to get the fire to go downhill and meet the fire that is already burning. That creates a zone of burned material so that there is nothing left for the fire to burn. If you do it right, once your fire reaches the existing fire there is nothing left to burn. The fire goes out. The fire is 50 miles around but on that one mile stretch, on that one ridge, you have stopped that one flank of forward movement of the fire. If you do it right you can do that on every side of the fire. You can contain the fire and stop its movement. That does not mean there are not places in the middle still burning. 

## The Goal is Containment

When you are fighting a wildfire you are not trying to put the fire out. You’re trying to contain it. The fire will still burn, that is what happened in the August Fire. There were trees still burning up with charcoal the following Spring in the snow. But since it was contained we were not worried about it. Because the fire could not spread beyond its boundaries. One million and 36,000 acres. The job of the wildland firefighter is not to put a fire out it is to contain it. How weather plays in: you have that daily explosion of the fire, the nightly decline, the morning decline.

But weather occurs at a larger scale. The cold front is a lot bigger. Then you would have a big blow up. The fire would grow by 50,000 acres in a day. Then for several days through you had the daily cycle, it never grows as fast as it did. But then there is a different system that comes in with the wind. And that wind changes everything.

If you look at it from a daily level, and it grows one day 1000 acres from wind. It is growing about 1000 acres a day. Then, a new weather system comes in, and it blows everything up again. Instead of 30,000 acres, it’s 200,0000 acres in one day. Instead of growing 1000 acres in a day, it has jumped. From a firefighting standpoint, there is not really much you can do. You are putting in line, hoping that, when it reaches the fireline, it will be in the condition to stop. People are sometimes so afraid of fire that they won’t let firefighters do their job and do backburns, which makes it worse. 
There are a ton of fire models, but I suspect most of them are tuned to North America. I assume you want to use remotely sensed data.

The next day the inversion layer lifts, it pushes off the inversion layer, there is fresh air, and that moves the fire. 

## Data and Calculations Including Linear Regression

The basic question is trying to figure out the combination of conditions that lead to faster fire growth. You have a ton of data on topography and weather. Steepness aspects, all aspects of weather. Satellite heat data - infrared data is the most important. Satellite based infrared data that looks at the size of the fire. I would want to use daily or hourly imagery to calculate how fast the fire is moving. You can say this fire was 5 acres today, now it is 30 acres. You can figure out the rate of fire spread from that. If you can figure out the rate of fire spread over every pixel, then you can correlate that fire spread to every aspect of the ground, like fuel, which you can also get from satellite imagery. I would want to correlate all of this with rate of spread. 

Since the fire grew from 50 acres to 500 acres, it grew over this ring on November 22 at the rate of x number of acres per hours. Then I would ask a question of what the fuel type in that area was, what was the typography in that area. If I was doing basic linear regression, I would say: the average slope in that zone was this. I would say: does the slope of the ground correlate to the speed that it is going. Does steeper ground lead to faster growth. The answer for that is obviously yes. 

## Predicting Where to Dig the Fireline

With Machine Learning you could potentially tie in every single aspect. You could train the AI on all of the data that controls fire behavior: fuel, topography, data. You could train AI on all of the satellite imagery, the fire conditions on the ground to the rate of spread. AI could do a pretty good job at predicting how fast that fire would burn on a particular flank of the fire. I think if we knew that, it could be really valuable. We could then determine where to put the fireline. We want to put the fireline far enough away so that the workers don’t get burned but not so far away that the weather changes before the fire gets there.***You can't put the fireline about 20 feet in front of the fire. Note from Ashley: I need to fact check this one sentence with him, I can't read what I have***. 

If you have got to control a fire whose perimeter is 1 mile, and the fire is going at 1 inch per second, then you could predict where to put that fireline. If you can build a fireline at 1 mile an hour...

You want to build the fireline such that at the exact moment that the fireline is done the fire touches to fireline, like catching the fire. 
If we do not build it fast enough, the fire will burn over it. If we build it too fast or too far from the fire, by the time the fireline is done, the fire has not stopped burning. Ideally, we want the fires as small as possible. We have to build the fireline as close to the fire as we possibly can. It takes time to build that fireline. If it is a fire that is 50 miles in circumference we are also needing to factor in how long it takes to ship in another bulldozer from another part of the country. I want to know how fast this fire is growing. Machine Learning needs to say, at this pixel, I need to know, will this fire grow at this speed? So that I can build the fireline in the right place.

*This is a fire triangle:*
heat, oxygen, and fuel

*This is a fire behavior triangle:*
weather, fuel and terrain

### How to Cite
Ashley Rice. *Interview with a Wildfire PIO and Volunteer Firefighter, Redding, California.* Zenodo (2025). https://doi.org/10.5281/zenodo.17247725  

See [ORCID profile](https://orcid.org/0009-0001-5972-2257) for related works.
