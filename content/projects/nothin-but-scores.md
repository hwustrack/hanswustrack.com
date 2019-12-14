---
title: "Nothin But Scores"
date: 2019-12-13T13:23:39+13:00
---

[Nothin But Scores](https://nothinbutscores.com/) is a service that posts final scores from sporting events to dedicated Twitter accounts. I wanted to be able to browse Twitter and get updates on the teams I follow, without getting spammed with all of the pre/post game coverage that sports Twitter accounts normally have.

The backend is built on [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/). There is a function for each league that's tracked. When each of the functions runs on its specified interval, it will loop through each of the teams that are currently being tracked, ask the API if there are any games for that team today, and if there are, if it is complete. If it is complete, it will check if that score has already been posted on Twitter. If it hasn't, it will post the score for the recently completed game to the team's dedicated Twitter account.

For most of the leagues, I use [MySportsFeeds](https://www.mysportsfeeds.com/) to track the events and get the final scores. It's a great reliable service, that's free to start.

The main roadblock I've run into so far has been creating the Twitter accounts. It's obviously a manual process and they ask for a phone number when creating them, so I've started to run into issues with getting new ones created because it says my phone number is already in use. Hopefully, I'll be able to find a workaround as I do believe this project is in keeping with Twitter's Terms and Conditions.

Find your team to start following at [nothinbutscores.com](https://nothinbutscores.com/).