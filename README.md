# Dsc-PT04-Phase-3-Project
# MAJI NGO TANZANIAN WATER WELL PROJECT

![header-ngo.jpeg](attachment:header-ngo.jpeg)


Water is one of the three basic needs required for a human being to survive. Water, not only quenches your thirst but also is essential to keeping your body healthy and functioning properly e.g. It makes up almost 90% of blood and hence aid in all the bodily functions that blood carries out like regulating body temperature, it lubricates joints, dissolves minerals and nutrients to make them accessible to the body, etc. Without going into further biological detail we can see how important water is to a person.<a href="https://www.mayoclinichealthsystem.org/hometown-health/speaking-of-health/water-essential-to-your-body">Mayo Clinic Health</a>

With this in mind, most developing countries have a high poverty rate which means access to a necessity like water is low.
Tanzania (a counrty located in East Africa) has one such problem. Out of its population of 59 million people, 16 million people **(28% of the population)** lack access to safe water and with a growing population this number could potentially rise. Thus we see there is a need to give ready access to clean, drinking water to households all over the country.<a href="https://water.org/our-impact/where-we-work/tanzania/">water.org</a>

This is where **Maji NGO** comes in. **Maji NGO** Maji NGO is a Non-Governmental Organization dedicated to enhancing the welfare of people in African countries, firstly in **Tanzania** and then in other developing countries in the future. 

Why Tanzania first? Our focus on Tanzania is strategic; the country has already taken proactive steps by installing water pumps across various regions. Leveraging the support of the Tanzanian Ministry of Water and Taarifa, an open-source platform for crowd-sourced reporting and infrastructure issue management, **Maji NGO** have gained access to valuable data on these water pumps.The availability of this data allows us to analyze it to make inferences, meaningful insights an predictions with which we can approach our donors to show accountability of every shilling spent.

Maji NGO wants to now set up even more pump stations across the country to aid in more people having access to clean and safe water and furthermore help in repairing any pumps that have already been setup but have an issue that may or may not be affecting their functionality.

**Maji NGO** ,being a nonprofit that is fundraising for this project, wants to be prudent with the investment that goes into it and ensure nothing goes to waste at the expense of a household that could greatly benefit from it. Every single shilling should count as it can transform lives for the better.

The fundraisers (since they are the stakeholders) need to be shown this data-driven approach that allows us to make informed decisions about our interventions, ensuring that every investment yields tangible results. We want responsible usage of funds to guarantee the efficacy of everyone's efforts since no one likes to see their money go to waste.

In order for **Maji NGO** to carry out this project, we have set out the following objectives to guide us:
1. We want to setup long-lasting pumps so as to ensure more uptime and that the maintenance fees are not that high. This is due to the fact that if the pumps have low uptime, families benefit for a short period before going back to square one, and also funds may not always be readily available as there may be more pressing issues that the NGO needs to deal with. The more self-sustaining the pump is, the better for everyone.

2. Which pumps if setup will need a bit more maintenance than the rest, or rather what factors may increase the chances of a pump breaking down.

In summary, we want to know of those that have broken down, what are the lessons we can learn from them when setting up new pumps or even from the ones which have not, what can they teach us.

## DATA UNDERSTANDING

We start by opening the data-set from **Taarifa**. As mentioned earlier Taarifa is an open-source platform for crowd-sourced reporting and infrastructure issue management. This means that community members can use the platform to report various issues they encounter and provide more details.  By making the reporting and management process open and transparent, these platforms enhance accountability. Both community members and local authorities can see the reported issues, their status, and the actions taken, fostering trust in the system.

We start by importing the most commonly used libraries and then accessing the csv file just to have an overview of what we are working with.
Attached to this data is the following description on what all the columns contain to aid in understanding:
- **amount_tsh** - Total static head (amount water available to waterpoint)
- **date_recorded** - The date the row was entered
- **funder** - Who funded the well
- **gps_height** - Altitude of the well
- **installer** - Organization that installed the well
- **longitude** - GPS coordinate
- **latitude** - GPS coordinate
- **wpt_name** - Name of the waterpoint if there is one
- **num_private** -
- **basin** - Geographic water basin
- **subvillage** - Geographic location
- **region** - Geographic location
- **region_code** - Geographic location (coded)
- **district_code** - Geographic location (coded)
- **lga** - Geographic location
- **ward** - Geographic location
- **population** - Population around the well
- **public_meeting** - True/False
- **recorded_by** - Group entering this row of data
- **scheme_management** - Who operates the waterpoint
- **scheme_name** - Who operates the waterpoint
- **permit** - If the waterpoint is permitted
- **construction_year** - Year the waterpoint was constructed
- **extraction_type** - The kind of extraction the waterpoint uses
- **extraction_type_group** - The kind of extraction the waterpoint uses
- **extraction_type_class** - The kind of extraction the waterpoint uses
- **management** - How the waterpoint is managed
- **management_group** - How the waterpoint is managed
- **payment** - What the water costs
- **payment_type** - What the water costs
- **water_quality** - The quality of the water
- **quality_group** - The quality of the water
- **quantity** - The quantity of water
- **quantity_group** - The quantity of water
- **source** - The source of the water
- **source_type** - The source of the water
- **source_class** - The source of the water
- **waterpoint_type** - The kind of waterpoint
- **waterpoint_type_group** - The kind of waterpoint

We notice that the data frame doesn't have the column with the dependable variable we are to use `status_group`. This variable is located in another csv file. 
We proceed to access this other file

Once our data finally looks clean enough to be worked on and carry out some analysis and modeling

## EDA

With our clean data set we can now proceed and carry out some exploratory data analysis to better understand.

We start off by visualizing the number of pumps that work, those that are working but need repairs and those that are not working.

![download](https://github.com/Ones-Muiru/Dsc-PT04-Phase-3-Project/assets/128042986/fc5a7d5b-5df6-4291-ab01-f0ac4f0771f8)

We can see most of the pumps are still functional even though some of them need repairs.

Next, we want to check the correlation of the numerical columns as you can't check colinearity on columns that do not have numbers.

![download](https://github.com/Ones-Muiru/Dsc-PT04-Phase-3-Project/assets/128042986/105d1018-bfd5-43be-9417-ac7465ca76cd)

Most of the columns have weak positive or negative correlation to each other. The strongest positive correlation is between district code and region code. They have a correlation of **0.72**. Nothing of note stands out.

We then proceeded to see if there is a relation between gps_height (height above sea level) and amount_tsh(amount of water available at water point)

![download](https://github.com/Ones-Muiru/Dsc-PT04-Phase-3-Project/assets/128042986/d70b8e45-ae27-4a25-95ab-0fcce1d7854d)

We can see that even as the altitude increases there isn't a necessary increase in the amount of water available despite a few outliers. This shows we will find water at all altitudes the amount is what may not be enough.

We then proceeded to visualize the population distribution in the different regions.

![download](https://github.com/Ones-Muiru/Dsc-PT04-Phase-3-Project/assets/128042986/28cafaca-4541-4cd2-a1de-5bf591c2d486)

We can see the region with the highest population is **Kigoma** and the one with the least is **Shinyanga**. This can help guide which areas are in more need of functional pumps due to more people living there.

We now want to see if the age of the pump has any relation to its functionality.

We start by changing the data type of the `construction_year` column so that we can easily plot it.

![download](https://github.com/Ones-Muiru/Dsc-PT04-Phase-3-Project/assets/128042986/e8e16a56-3a80-46fd-b4f4-8a066e92ae1a)

We can see that most of the pumps set up earlier are non-functional and most of the more recent ones are still working. This shows what we suspected that the pump will wear down with age. The older it is the more likely it is to have broken down.

We now proceed to check the relation between `population` and `payment_type ' through a violin plot.

![download](https://github.com/Ones-Muiru/Dsc-PT04-Phase-3-Project/assets/128042986/a235f70f-d230-4c35-ba9b-9e5a2af531e3)

We see that the pumps where you don't have to pay to use them, there is a high population. This makes sense as people will tend to use pumps that are free.
The pumps where you pay on failure there is the least amount of population.

Finally, we want to see the functionality of pumps in the different regions.

![download](https://github.com/Ones-Muiru/Dsc-PT04-Phase-3-Project/assets/128042986/97ab543e-7102-41ab-b868-785cdb1f0476)

This graph shows us regions with high functionality. These are the regions where we would want to set up future pumps. These regions are like **Iringa** and **Kilimanjaro**.

## CONCLUSION

Let's start by recalling the objectives that are guiding us:

1. We want to setup long-lasting pumps so as to ensure more uptime and that the maintenance fees are not that high
2. Which pumps if setup will need a bit more maintenance than the rest, or rather what factors may increase the chances of a pump breaking down

We want a model that can help us in predicting with high accuracy the factors that affect the functionality of the water pumps. With this, we can make data-driven decisions when setting up the pumps funded by **Maji NGO**.

I believe the **forest** model among all our models had the best results on the training data and can thus be used with **79.62** accuracy to determine which factors affect the water pump functionality

### Next Steps

- Some of the columns had a large amount of missing data, If it is possible to collect this data from the field that would   greatly improve model performance in terms of making inferences

- Run more models that have not been run in this notebook and counter-check with the ones in this notebook.

Work Done by Onesphoro M. Kibunja
