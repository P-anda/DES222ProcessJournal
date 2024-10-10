
## DES222 - Task 2: Process Journal

This project focuses on addressing a common challenge that all dog owners face: toilet training. Specifically, it's aimed at those who live in small apartments or townhouse complexes where access to a yard isn't readily available for their canine companion.

<img style="display: block; margin: auto;" src="images/logo.png"/>

Introducing the Paw Bell: a doorbell for dogs that connects to your Wi-Fi network, sending notifications directly to your mobile device. This helps train your dog to signal when it’s time to “go,” ensuring you're always aware—no matter where you are in the house.

<img style="display: block; margin: auto;" src="images/benji/benjidoor.jpg"/>

## Research

### Product 1 - Pet Talking Buttons
The most basic version of a dog doorbell, these buttons play a sound through a built-in speaker when pressed. A notable feature is the ability to record custom sounds or voice cues. However, the downside is the lack of volume control, which means the effectiveness depends entirely on the owner's ability to hear the sound. This can make training difficult, especially if the button is located in another room or out of earshot (as seen in the image above).

<img style="display: block; margin: auto;" src="images/pet-talking-buttons.png"/>

### Product 2 - Smart Bell by Mighty Paw
This product builds on the basic button design by adding a receiver that plugs into a wall outlet. When one of the connected buttons is pressed, the receiver plays a tone. The buttons act as transmitters and don't require charging or batteries because they use a micro-generator, which creates enough power when pressed to send a signal. However, a limitation of this system is that the receiver and buttons must be within range of each other, and interference or distance can reduce its reliability.

<img style="display: block; margin: auto;" src="images/product-1.png"/>

### Product 3 - Echo Buttons
Although not designed for pets, Echo Buttons interact with Alexa and other compatible Echo devices to trigger Smart Home routines or play games. These buttons use two AAA batteries and can connect up to four devices via Bluetooth. They’ve since been discontinued, as most of their functions can be performed through apps or voice commands, making them largely redundant.

<img style="display: block; margin: auto;" src="images/echo-buttons-2.png"/>

### Concept
<img style="display: block; margin: auto;" src="images/logo.png"/>
<img style="display: block; margin: auto;" src="images/house.png"/>


    Since dogs can’t use smartphones or give voice commands, a button system is an ideal way for them to interact with technology. My goal is to combine the concepts from the products above to create a dog bell that alerts owners when they’re less likely to notice their pet—like when they’re listening to music or working on a computer.

The button will connect to the home Wi-Fi and trigger a response that’s sent to a webpage, either on your computer or phone.

<img style="display: block; margin: auto;" src="images/diagram-1.png"/>



## Pre-Development

Before I could get started on making the product I decided figure out exactly what components and materials I needed. 


Since the talking buttons (from Product 1) came in a four pack I was able to dissasemble one to see if I can reuse the button for my
prototype. The button is the perfect size and dosn't require a lot of downward pressure to activate.
<img style="display: block; margin: auto;" src="images/benji/buttons-use.jpg"/>

At first I was going to use the Micro:Bit and an ESP-01 wifi module to connect to a network and send a HTTP request to a web interface. However after
some research I found a better all in one solution.
<img style="display: block; margin: auto;" src="images/part-2.jpg"/>

This Wi-Fi board features flash memory to send a request to an external service acting as a webhook that will call when the button is pressed.

<img style="display: block; margin: auto;" src="images/part-3.jpg"/>

**How it might work?**
1. ESP8266 Setup: When the button is pressed, the ESP8266 sends an HTTP request to an external webhook.
2. Webhook Service: Use a service like IFTTT, Zapier, or a custom backend (like Firebase Functions) to receive the request.
3. Webpage on GitHub: The webpage uses JavaScript to periodically check for notifications or to listen for an event and play the sound when notified.


**Possible Issues**

- Battery Life: To send requests to the web, the button will need a constant Wi-Fi connection, which could lead to quicker battery depletion.
I need to experiment with 'sleep' modes to ensure the device is only on when needing to send data.

- Accessibility: The website receiving the notification will need to remain open to ensure the message is received in real-time. 
Also due to the limitations of GitHub Pages (being static), we can't directly have the ESP8266 communicate with it in real time.
The use of IFTTT as a bridge should allow us to bypass this limitation by leveraging external services.
