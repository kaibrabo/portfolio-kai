---
layout: post
title: Chatta
thumbnail-path: "img/chatta_home.png"
short-description: a Messaging Simplified built using AngularJS.

---

{:.center}
![]({{ site.baseurl }}/img/chatta_home.png)


## Explanation

In today's main forms of communication, messaging is the primary way for many people to connect with each other.  

Introducing Chatta!

The main purpose for the creation of Chatta was to learn the Front-End functionality between an AngularJS application and Google's FireBase Database.  Built on AngularJS's Javascript framework made for efficient workflow and smooth UX.  

My role was to design and implement a functional messaging application using AngularJS framework, FireBase Database to track users and messages.


## Problem

Keeping connected is a deeply fundamental part of being a person in today's society.  

## Solution

Chatta creates an environment to efficiently communicate between users and even groups of users at any time!  The user interface has been optimaized with the latest technologies and backed by Google's support.

The most crucial components of the application were the (chat) Rooms and the users, who had saved sessions using cookies.

When a user is signed on, every message is saved using a unique ID created by each message, linking the users who are communicating.  This is the brilliance of FireBase!

Switching between chat rooms are a seamless transition due to the fluidity of the AngularJS framework.

Room Controller:
{% highlight javascript %}
function RoomCtrl($uibModal, Room, Message, $cookies, $firebaseAuth){

		var provider = new firebase.auth.GoogleAuthProvider();
		var auth = $firebaseAuth();

		this.title = "Messages";
		this.rooms = Room.all;
		this.currentRoom = null;
		this.messages = null;
		this.currentUser = $cookies.get('ChattaCurrentUser');
		this.newMessage = {
			content: null,
			roomId: null,
			sentAt: null,
			username: null
		}

		this.addChat = function(){

			$uibModal.open({
				templateUrl: '/templates/modal.html',
				controller: 'ModalInstanceCtrl',
				controllerAs: 'modal',
				size: 'sm'
			});
		};

		this.setCurrentRoom = function(room){
			this.currentRoom = room;
			this.messages = Message.getByRoomId(room.$id);
		};

		// send message from input
		this.sendMessage = function() {

			this.newMessage.roomId = this.currentRoom.$id;

            this.newMessage.username = this.currentUser;

			this.newMessage.sentAt = firebase.database.ServerValue.TIMESTAMP;

            Message.send(this.newMessage);

			document.getElementById("textarea").value = "";

			console.log(this.newMessage.content, "message content");

			console.log(this.newMessage.roomId, "room id");

			console.log(this.newMessage.sentAt, "Roomctrl sentAt");

		}

		this.signOut = function() {
			firebase.auth().signOut().then(function(returnedObject) {

			}, function(error) {
				// An error happened.
			});
            $cookies.remove('ChattaCurrentUser', this.username);
        }
	}

	angular
		.module('chatta')
		.controller('RoomCtrl', ['$uibModal', 'Room', 'Message', '$cookies', '$firebaseAuth', RoomCtrl]);
{% endhighlight %}

Room.js:
{% highlight javascript %}
function Room($firebaseArray) {

        var Room = {};
        var ref = firebase.database().ref().child("rooms");
        var rooms = $firebaseArray(ref);
        
        Room.all = rooms;

        Room.add = function(room){

            rooms.$add(room);
        };

        return Room;
    }

    angular
        .module('chatta')
        .factory('Room', ['$firebaseArray', Room]);
{% endhighlight %}

Cookies Controller:
{%highlight javascript%}
(function() {
    function CookiesInstanceCtrl(Room, $uibModalInstance, $cookies, $uibModal, $firebaseAuth) {

        var provider = new firebase.auth.GoogleAuthProvider();

        this.createUsername = function() {
            // disables signUp if input is empty
            if (!this.username || this.username === ''){
                return;
            }

            // if a username is entered...
            // assigns the cookies current user w/ this.username
            $cookies.put('ChattaCurrentUser', this.username);

            $uibModalInstance.close()

            window.location.reload(true);

        }

        this.signin = function(){

            firebase.auth().signInWithPopup(provider).then(function(result) {
                // This gives you a Google Access Token. You can use it to access the Google API.
                var token = result.credential.accessToken;
                // The signed-in user info.
                var user = result.user;
                console.log(result.credential.accessToken, "token");
                console.log(result.user, "user");
                console.log(user.displayName, "username");

                this.username = user.displayName;

                $cookies.put('ChattaCurrentUser', this.username);

                $uibModalInstance.close()

                window.location.reload(true);

            }).catch(function(error) {
                // Handle Errors here.
                var errorCode = error.code;
                var errorMessage = error.message;
                // The email of the user's account used.
                var email = error.email;
                // The firebase.auth.AuthCredential type that was used.
                var credential = error.credential;
                // ...
            });

        };
    }
    angular
        .module('chatta')
        .controller('CookiesInstanceCtrl', ['Room', '$uibModalInstance', '$cookies', '$uibModal', '$firebaseAuth', CookiesInstanceCtrl]);
})();
{%endhighlight%}

## Results

AngularJS enabled a simplified working app, reduced amount of Vanilla JS, made the code clearer for anyone looking to improve on the app.  Refactoring the app created a richer user experience, showing the app has been well-built.

> SPA's, Single Page Applications, work efficiently using templates that are loaded when needed, which only changes the specific section and not the whole page.  This increases efficiency and an immaculate user experience.

The engine of the framework are the controllers.  They drive the features on templates, from sorting albums to the fluidity of the player bar transitions. The player bar utilizes directives and services that uses AngularJS's two-way binding.


## Conclusion

I was underestimated the learning curve of AngularJS.  This project is the first introduction to the framework, AngularJS is a very efficient tool in creating SPA's.  Taking into consideration that I now know AngularJS, it will be a framework I will readily use on any new project that requires AngularJS.