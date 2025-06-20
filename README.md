<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Module 6 - Fictional Dogs</title>
</head>
<body>
    <h1>Fictional Dogs from Animated TV Shows</h1>
    <div id="dogList"></div>
    <hr>
    <div id="dogInfo"></div>

    <script>
        // Constructor function for dog objects
        function Dog(name, breed, origin, personality, mySound, canTalk) {
            this.name = name;
            this.breed = breed;
            this.origin = origin;
            this.personality = personality;
            this.mySound = mySound;
            this.canTalk = canTalk;

            this.myGreeting = function() {
                let talkMessage = this.canTalk ? "I can talk!" : "I cannot talk.";
                return `Hello! My name is ${this.name}. I am a ${this.breed} from '${this.origin}'. I am known to be ${this.personality}. I usually say: "${this.mySound}". ${talkMessage}`;
            };
        }

        // Create dog objects
        let scoobyDoo = new Dog("Scooby-Doo", "Great Dane", "Scooby-Doo, Where Are You!", "goofy and cowardly", "Ruh-roh!", true);
        let brianGriffin = new Dog("Brian Griffin", "White Labrador", "Family Guy", "sarcastic and intellectual", "I'm Brian, nice to meet you.", true);
        let courage = new Dog("Courage", "Beagle", "Courage the Cowardly Dog", "timid but brave when needed", "AAAAAH!", false);

        // Store the dogs in an object for easy access
        let dogs = {
            "Scooby-Doo": scoobyDoo,
            "Brian Griffin": brianGriffin,
            "Courage": courage
        };

        // Display properties of each dog using for...in loop
        let output = "";
        for (let dogName in dogs) {
            output += `<h2>${dogName}</h2><ul>`;
            for (let prop in dogs[dogName]) {
                if (typeof dogs[dogName][prop] !== "function") {
                    output += `<li>${prop}: ${dogs[dogName][prop]}</li>`;
                }
            }
            output += "</ul>";
        }
        document.getElementById("dogList").innerHTML = output;

        // Prompt user to select a dog
        let userChoice = prompt("Type a dog's name: Scooby-Doo, Brian Griffin, or Courage");

        // Display greeting or error message
        if (dogs[userChoice]) {
            document.getElementById("dogInfo").innerHTML = `<p>${dogs[userChoice].myGreeting()}</p>`;
        } else {
            document.getElementById("dogInfo").innerHTML = `<p style="color:red;">Sorry, no dog with that name exists in our list.</p>`;
        }
    </script>
</body>
</html>
