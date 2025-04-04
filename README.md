UNAUTHORISED_ACCESS_DETECTION
This project implements a real-time unauthorized access detection system using webcam capture, facial recognition, and email alerts. It is designed to enhance login security by identifying the user attempting access and notifying the system owner in case of suspicious activity.

![Project flowchart](images/flowchart.png)


When the program starts, it immediately activates the webcam to capture an image of the person currently in front of the system. This image is stored and processed using a face detection algorithm. At the same time, the program fetches the user's geographical location based on their IP address using an external API.

Next, the system prompts the user to enter a username and password. The entered username is checked against a predefined list of users. If the username is invalid, the program exits with a message. If the username is valid, the user is allowed up to three attempts to enter the correct password.

During this process, the system monitors and handles different scenarios:

If the user enters the correct password on the first or second attempt, and the face detected matches the expected user, the login is marked as successful. No email is sent, and access is granted.

If the correct password is entered, but the captured face does not match the expected user (i.e., someone else is logging in), the system flags it as suspicious. Although the login succeeds, an email alert is sent to the owner’s registered email with the captured image and location, notifying them of a possible unauthorized login.

If the password is entered incorrectly three times, the system checks the captured face:

If the face matches the owner's face, it assumes the real user simply forgot their password. In this case, the system sends an email with a password reset link to the registered email.

If the face does not match the owner's face, it is treated as an unauthorized access attempt. The system sends a warning email with the captured image and location to alert the owner about the intrusion.

Each email includes:

The number of failed login attempts

The time of the access attempt

The location of the user

A captured image of the person attempting access (if unauthorized)

This layered security approach helps to protect sensitive systems by alerting users to intrusion attempts and offering password recovery options when appropriate, all while visually verifying the person at the keyboard.


