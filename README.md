# MLB.TVguide

-docker pull command:



```

docker pull ghcr.io/rice9797/mlb-scraper:latest

docker run -d --restart unless-stopped --name mlbtvguide -p 9797:9797 -e TZ=America/Chicago ghcr.io/rice9797/mlb-scraper:latest

```



-accepted TZ=

	•	Eastern: America/New_York
	•	Central: America/Chicago default
	•	Mountain: America/Denver
	•	Pacific: America/Los_Angeles
	•	Alaska: America/Anchorage
	•	Hawaii: America/Honolulu
	•	Arizona (no DST): America/Phoenix


-this container is designed for use with channels dvr. 

-this container does not provide video of games from mlb.com. it is simply for assigning alternate mlb guide data to an existing source ie.(mlbserver) that provides the actual video feed. 

-this is an alpha version for testing purposes. use at own risk!!

-endpoints are:

source m3u:    http://ip.of.docker.machine:9797/mlb.m3u 


xmltv guide data:       http://ip.of.docker.machine:9797/mlbguide.xmltv



-for use in channels dvr:

1.  add a custom channel and name the source
2.  under stream format choose MPEG-TS
3.  under source choose URL and insert  http://ip.of.docker.machine:9797/mlb.m3u
4.  under options choose refresh daily, ignore channel number from m3u, choose a starting channel number (i suggest a very high starting channel out of the way), prefer channel logos from m3u, and finally no stream limit.
5.  under xmltv guide data insert http://ip.of.docker.machine:9797/mlbguide.xmltv
6.  choose a refresh of 2 hours or schedule you prefer 
7.  click save and the source will be generated

IMPORTANT!!

8.  IMPORTANT!! click manage lineup under the new source and void out all the channels. this will prevent channels from trying to record from the dummy channels in the m3u. IMPORTANT!!

9.  if you have already created the mlbserver source inside of channels dvr, i have found you need to remove the custom source and remake it with nothing inside the url xmltv guide data box, choose a refresh period of 2 hours and save. if you havent made the mlbserver source in channels dvr yet, when you make the mlbserver source leave the xmltv guide data section empty. choose refresh every 2 hours. 
11.  now you can assign the guide data to the mlbserver source from this mlb.tvguide container
12.  choose the manage section on the mlbserver source and then choose set provider(or change provider). next choose pick existing and then choose this projects custom source name. 
13.  click manage on the mlb server again, select manage lineup, click the pencil on each team and select the teams that correspond with each other.
14.  in channels go to settings>live tv & dvr>guide data maintenance srop down>fetch guide updates. if guide data still doesnt populate you may need to select delete and recreate database from that same dropdown. 
  
