---
layout: post
short_title: Spotibot
title: "Spotibot"
description: "Spotibot: A Facebook Messenger Chat Bot to retrieve Spotify links"
icon: spotibot.jpg
github: https://github.com/NakuraMino/Spotibot
date: 2019-12-20
show_date: false
ready: false
---

![Spotibot Demo](/assets/images/projects/spotibot.jpg){:class="blog-img"}

## Introduction
Spotibot is a Facebook Messenger Bot. A user can send a message in the format "Artist:_ Song:_ “ and the chatbot will return a spotify link of the song. I like to listen to a lot of music and often want to share these songs with my friends. I found it extremely inconvenient to switch back and forth between the Spotify app and the Messenger app, so I decided to make a messenger app that would retrieve a shareable link for me.

## How I coded this project
The first resource I turned to was this [Facebook Messenger Bot Tutorial](https://www.youtube.com/watch?v=uU4pjtcbFeg&list=PLyb_C2HpOQSC4M3lzzrql7DSppTeAxh-x) by the Indian Pythonista. After I completed a simple echo chatbot, I created a Spotify Developer Account and started using the Spotify API to retreive songs. I parsed the JSON data to first find the artist, and then searched the artist’s albums until I found the track that matched the user’s request. The program is uploaded onto the Heroku Cloud Platform. The Heroku link was then connected to the Facebook page.