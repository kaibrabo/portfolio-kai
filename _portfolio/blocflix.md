---
layout: post
title: BlocJams
thumbnail-path: "img/BlocJams - AlbumView.png"
short-description: BlocJams is a Spotify replica to stream your music library.

---

{:.center}
![]({{ site.baseurl }}/img/BlocJams - Landing.png)

{:.center}
![]({{ site.baseurl }}/img/BlocJams - Landing2.png)

## Explanation

Introducing BlocJams, a streaming service for your music library. BlocJams eliminates the need to sync your phone to your computer, take up memory on the device and allows remote listening anywhere on any device.  There are streaming services like Itunes and Spotify, but what should you do with all the music you've acquired throughout the years? This app is of most use to anyone who would like to listen to their entire music library without having to sync to a computer.  With streaming, another benefit is use on any device connected to internet.  

My role was to design and implement a functional music player that retrieves and plays an existing music library.

{:.center}
![]({{ site.baseurl }}/img/BlocJams - ListAlbums.png)

## Problem

There is a pursuit to become completely disconnected from wires and using up memory to listen to music.  Although devices are gaining more memory, the goal was to eliminate the need to worry about filling up memory.  Streaming allows us to automatically sync our music library to a cloud server, where it can be accessed by any device with internet connection.

{:.center}
![]({{ site.baseurl }}/img/BlocJams - AlbumView.png)

## Solution

BlocJams will allow users to have their entire library asynchronous to any device loaded with the app.  With the demand of a fluid user experience, I used AngularJS for this project.  AngularJS allows smooth transitions without reloading the pages, yet only loads the right information when needed, making it ideal for efficiency.  The explicit HTML directives and services made the app perform seamlessly when transitioning between templates, as well as helped with the debugging process.

## Results

AngularJS enabled a simplified working app, reduced amount of Vanilla JS, made the code clearer for anyone looking to improve on the app.  Refactoring the app with create a richer user experience, showing the app has been well-built.

> SPA's, Single Page Applications, work efficiently using templates that are loaded when needed, which only changes the specific section and not the whole page.  This increases efficiency and an immaculate user experience.

The engine of the framework are the controllers.  They drive the features on templates, from sorting albums to the fluidity of the player bar transitions. The player bar utilizes directives and services that uses AngularJS's two-way binding.

{% highlight javascript %}
SongPlayer.play = function(song) {

    song = song || SongPlayer.currentSong;

    if (SongPlayer.currentSong !== song) {

        setSong(song);

        playSong(song);

    } else if (SongPlayer.currentSong === song) {

        if (currentBuzzObject.isPaused()) {

            currentBuzzObject;

            currentBuzzObject.play();
        }
    }
};
{% endhighlight %}

## Conclusion

I was underestimated the learning curve of AngularJS.  This project is the first introduction to the framework, AngularJS is a very efficient tool in creating SPA's.  Taking into consideration that I now know AngularJS, it will be a framework I will readily use on any new project that requires AngularJS.
