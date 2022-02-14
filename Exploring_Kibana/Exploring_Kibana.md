---

1. Add the sample web log data to Kibana

2. Answer the following questions:

- In the last 7 days, how many unique visitors were located in India?

	**223**

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.1.png)

- In the last 24 hours, of the visitors from China, how many were using Mac OSX?

	**64**

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.2.png)

- In the last 2 days, what percentage of visitors received 404 errors? How about 503 errors?

	**404 = 25%**

	**503 = 0%**

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.3.png)

- In the last 7 days, what country produced the majority of the traffic on the website?

	**China 20.0%**

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.4.png)

- Of the traffic that's coming from that country, what time of day had the highest amount of activity?

	**12pm**

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.5.png)

- List all the types of downloaded files that have been identified for the last 7 days, along with a short description of each file type (use Google if you aren't sure about a particular file type).

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.6.png)

gz: gzip, compresses an archive using an algorithm.

css: programming language used for web pages.

zip: compressed archive.

deb: debian, linux compressed package.

rpm: similar to deb, but used for red hat enterprises.


3. Now that you have a feel for the data, Let's dive a bit deeper. Look at the chart that shows Unique Visitors Vs. Average Bytes.

- Locate the time frame in the last 7 days with the most amount of bytes (activity).

 	**Feb 6, 2022 @ 21:00:00:00 -> Feb 7, 2022 @ 00.00.00.0010,735.667 Avg. bytes**
 
- In your own words, is there anything that seems potentially strange about this activity?

	**There are 2 suspicious visitors.**

4. Filter the data by this event.

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.7.png)


- What is the timestamp for this event?
	
	**Feb 6, 2022 @ 21:00:00:00 -> Feb 7, 2022 @ 00.00.00.00**
- What kind of file was downloaded?
	
	**Zip and rpm**
- From what country did this activity originate?
	
	**China and India**
- What HTTP response codes were encountered by this visitor?
	
	**200**

5. Switch to the Kibana Discover page to see more details about this activity.

- What is the source IP address of this activity?

	**73.105.236.24 & 35.143.166.159**
	
- What are the geo coordinates of this activity?

	**"lat": 42.99821222, "lon": -74.32955111**
	**"lat": 43.34121, "lon": -73.6103075**

- What OS was the source machine running? 

	**Linux**
	
- What is the full URL that was accessed?

	**https://www.elastic.co/downloads/apm & https://artifacts.elastic.co/downloads/kibana/kibana-6.3.2-windows-x86_64.zip**

- From what website did the visitor's traffic originate?

	**http://facebook.com/success/jay-c-buckey & http://twitter.com/success/maksim-surayev**

![](https://github.com/JasonMartin87/Jason-Martin-Project-1/blob/main/Exploring_Kibana/images/2.8.png)

6. Finish your investigation with a short overview of your insights.

- What do you think the user was doing?

	**One was downloading rpm files while the other was downloading a zip file. **
	
- Was the file they downloaded malicious? If not, what is the file used for?

	**Unlikely, the zip file is a Kibana installations for windows while the other is an installations for Metricbeat.**

- Is there anything that seems suspicious about this activity?

	**Unless if we are able to see the files, there’s no way to tell unless the source is legitimate and trustworthy.**
	
- Is any of the traffic you inspected potentially outside of compliance guidelines?

	**Looks normal and nothing out of the ordinary.**
