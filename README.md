# welfare-ai
Note: Video demo shows the features of our product but doesn't really explain how they were used. The following explains that information.
https://youtu.be/bbONkVBQmPM

## Inspiration
More than 2 in 5 US residents reported symptoms of depression and anxiety during the pandemic. As students, we have realized that a lot of our time is spent in front of a laptop and first-hand watched our mental health deteriorate during the pandemic. That’s why having an application like WelfareAI is so important!

## What it does
WelfareAI can do many things. The goal of our product was to provide a product that could maintain the welfare of the user as they spend their time in front of a laptop. The features of our product are numbered below:

1. First, it can register the "mood" of a person. This is very important to provide automated action and suggestions from the website and to the user. The product can detect a total of 4 moods: happy, sad, angry, and surprised. With different moods, the website can perform different actions. If the user is happy, the website suggests if it should play the user's favorite spotify playlist. If the user is sad, the website suggests if it should tell the user a joke and play upbeat music. It can also ask "check-up" questions. If the user is angry, the website can display a 10 second timer for the user to cool down with and play soothing, classical music. Because all actions were covered in the first 3 moods, and there really is not much to do if a user is surprised, the website does nothing if the user is surprised. After suggesting actions (by speaking them out loud) the website awaits a "YES" or "NO" confirmation before proceeding.
2. Second, it can track the movement of the user's eyes. This was used for "YES" or "NO" gestures, which allows the user to accept or decline actions the website wants to perform. Additionally, it is used to check if the user is concentrated on his work (only if he has concentration mode on) or if the user is looking at something else (such as their phone). The website can alert the user if this occurs.
3. Third, it can detect and count the number of blinks the user does in a minute. It is very important to blink frequently to reduce eye strain, and people often don't do this enough when they are concentrating on their device. The website alerts the user to blink more if he or she hasn't done more than 15 blinks in the last minute.
4. Finally, it can keep track of two important things: water intake and break times. According to the Mayo Clinic, it is advised to drink 1 cup of water every hour. The product we created keeps track of this and alerts the user every hour to drink water. Additionally, it is also advised to take a 15 minute break every 2 hours a person spends on a digital device. Therefore, the product keeps track and alerts the user of this as well.

## How we built it
Website:
The website was built using a Bootstrap framework. Additionally, a Firebase backend was added to allow for users to sign up and login to the website. This can also be connected to the Python code to allow for all outputs of the Python code to be displayed on the website. This also allows for the user to save personal preferences, such as weight, height, etc which contributes to the calculation of when the user needs to drink water, how often they need a break, etc. (this still needs to be implemented).

Machine Learning Models and Logic Code:
The entire machine learning and logic code was written in Python. We used the fer2013_mini_XCEPTION model and haarcascade_frontalface model for mood classification,  and shape_predictor_68_face_landmarks model for eye tracking, gaze, gesture, and blink detection. The models for mood classification run of the frames of the real-time video and output the probabilites of each mood. We used this to define thresholds and classify the final user's mood. Next, we used specific point around the eyes for eye tracking and created a mask. Here, we segmented the dark portion of the eyes (pupil), and used this for eye tracking, displaying it on the video output. Next, for gaze detection, the code recognizes in which direction both eyes tracking point are pointing too and estimates the line of sight from the eyes. Then, for the gesture detection, the model tracks the coordinates on the eye tracking points and makes prediction based on the coordinates of whether the user nodded "YES" (y increases/decreases) or "NO" (x increase/decreases). Finally, for blink detection, the same points that outline the eye outputed by the shape_predictor model were used. When the points for the top eyelid and bottom eyelid touched, it was counted as a "blink".

## Challenges we ran into
-Web Development Team: This was our first time utilizing Firebase to implement the login authentication of our website. We took the time to learn and understand how Firebase works and successfully implemented it into our website. There had also been issues with pushing our changes to the repository through the VS Code Liveshare feature and after much deliberation, we decided to switch to a new repository instead. 

-Machine Learning Lead: There were many challenges. One was overlaying the video of different outputs, while maintaining proper quality of the image. To overcome this, we used to OpenCV library to specify the quality of each layer of the output. Another challenge was the speed. Initially, we had different models doing many of the tasks we wanted to do. However, in the end, we decided to accomplish most of our tasks by just using the shape_predictor_68_face_landmarks model by using different methods of masking, segementation, etc to get our different outputs.

## Accomplishments that we're proud of
We are proud of our logo that one of our teammates designed in Illustrator. We are also proud of our machine learning lead who created the mood detection and eye tracking system; they were also able to integrate that into the front-end.   

## What we learned
Our team discovered how to utilize Firebase into websites for login authentication, and developed a deeper understanding of HTML and CSS through the use of Bootstrap frameworks. Our team also developed a much deeper understanding of machine learning.

## What's next for Welfare-AI
We hope to continue improving the user interface of our website and its features. In addition, we hope to expand our machine learning model to recognize more body language. A future plan is to recognize different medical-related problems, such as seizures, and being able to alert other of what the user is experiencing. In doing so, we will be able to assist others with other emotional and physical needs.
