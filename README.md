# attendance-monitoring-using-facial-recognition


This is my attempt to make a Face recognition system for classroom or office attendance. The system is based on a special type of cnn architecture known as a siamese network. Such a network is trained to generate a very accurate and almost unique 128 vector given that the images of face which a are fed to the network are properly aligned and cropped.
Then another dense neural network is trained taking input these embeddings. The second neural network is only for classification purposes. Then the person who is identified by the system, his/her attendance in the system is incremented by 1.
When the system is closed, a excel file consisting of attendance of all the students is generated.



I have download the pretrained facenet model from nyoki-mtl github
This network is pretrained on a pretty large dataset, and produces a unique 128 dimensional vector for a particular face given the images fed to it are cropped to only the face region and are alligned. The input size of image for this netowrk is 160X160X3.

# Face Detection

Face detection is acheived by using haar cascades of opencv. Face detection haarcascade is used to detect the face and this detected region is fed to the embedding generator.
The second neural net

The second neural network has a dense architecture and is used for classification. The second neural network take input the 128 dimensional vector and ouputs the probability of the face to be one of the student.


# Updation of attendance

The database used is mongodb. Pymongo is used to add, delete records and also increment the attendance of the particular student. mongodb
csv file generation

After the application is closed, an excel file is generated. This excel file contains the attendance of all the student.
Requiremnents

# Installing the requirements

    Start your terminal and fire the commands.

pip install -r requirements.txt


Apart from all this you also have to install mongodb in your system.

# Watch it come alive on your own system

1)Install all the requirements

2)Make a folder named "people" without quotes

3)Now run Generating_training_data.py, when this runs enter the name of the person followed by a index beginning from zero for example, if I want to generate data for "ravi", I will write "ravi0" and for the next name write "secondname1", just make sure the index given to everybody is in increasing order. Now put all this folders into the people folder


4)Now in trainer.py change the number of classes according to number of folder and then run trainer.py

5)The model will be trained.

6)Now create a database using mongodb. Enter all the names with their attendance. This can be acheived by
a)create a data base named "new"
b)create a collection named "pa"
c)add the enteries. For eg db.pa.insert({"name":"Raja","attendance":0})


7)Now open recognizer.py and change the dictionary "a" and people according to your data. The key of array "a" is the index of the people and the data is a indicating variable which is used to indicate that in a particular session, if the person attendance has been taken.

8)Dictionary "people" is self explanatory.

9)Run recognizer.py to recognize people. Their attendance will be registered in the mongodb database.

# Suggestions
a) If you find some issues please report in the issues section.

b) If you liked the project please give a star. 
