# Meeting-Analysis

### Project Definition
-----
Since the use of daily scrums, where members of teams hold meetings to track progress of product/software development, The development process has become compatible with developing and delivering complex products in a structured manner. Recently, it has also established its place in other fields than software development. To optimize the outcomes of these daily scrums, team members should successfully deliver updates or demonstrate the work done since the last meeting, update the team on what they are going to do after the meeting, and describe the impediments faced by them. This project focuses on creating segments of individual speakers, define score for the meeting’s structure, and create clusters for speakers.

### Description
-----
The project evaluates meeting recordings and generates summary report to evaluate the structure of meetings and generating score for the structure of meetings. Firstly in the project, the video file is converted in to an audio file (.wav). Secondly, it reads signals from the audio file and get normalized segment feature statistics. Thirdly, it performs clustering of the audio based on an individual’s voice and then segment the audio. Fourthly, the program writes cluster signals into an audio file and calculates the score for the meeting. Finally, Audio chunks are created from the long audio and then it converts from speech to text.

### Audio Extraction
-----
The scrum meetings were recorded in MPEG-4 video format. To analyze several audio features it is required to extract audio from the video file. We used library named MoviePy to fetch audio from the video clip and further saved the data in the form of Waveform Audio File Format. The generated audio file could be used to analyze features of the audio file which may be useful in segmentation and clustering of the speakers. For the analysis of audio sample, we projected two characteristics i.e. zero-cross rate and energy against the successive frame samples. Zero-cross rate is the number of time the amplitude touches value zero while changing the frequency and energy represents the total magnitude of the signal. The representation of zero-cross rate is shown in the figure.
![alt text](/images/3.png)

### Clustering speakers
-----
The K means clustering method takes in a set of data points, where K specifies the number of inputs. The iteration is done on K different centroids where the nearest centroids or weights are mapped together. The cluster with the nearest centroid is picked. After this, the computation of new centroid is measured by averaging out the vectors of the new clusters. This technique was used to identify, label different speakers.
![alt text](/images/1.jpg)
  
* Speaker Diarisation is demonstrated below:  
![alt text](/images/2.png)

### Speech Recognition
-----
In the first instance, we used a SpeechRecognition library’s Google Speech Recognition to read the audio clusters that were formed and saved. In this process, we found that only partial conversation transcript was accurate, and we are required to have good accuracy overall. This was a setback for us, therefore, we tried a different approach. We broke the audio into parts whenever there was silence in the audio using the pydub [6] module. For this project, we detected and removed silence of 800 milli-seconds. If the silence occurred in-between two words, then the program would consider it as two different sentences. We have used Google Speech Recognition from the SpeechRecognition module, which processes the audio and returns the text, i.e., transcript of the audio. from the previously generated audio chunks from the audio cluster.

### Generating Report
-----
In the report, we have provided manual transcripts for each individual’s speech because the speech to the text module was not accurate. Firstly, we divided the speech into text and the text into a group of sentences. Secondly, each sentence is divided into a bag of words. The next step is to determine the tense of the words. Words can be a verb, a noun or an adjective, therefore we were looking for cluttering words into the past, present tense. Later, the program counted the number of occurrences of a total of past tense words with the total of future tense words. If past tense words were found, then the statement would be considered as the past tense and if future tense words were found, then the statement would be considered as the future tense. Besides, the program would also check for negative words in the sentences. For instance, if there is a word error, problem or issue occurred in a sentence then we consider that sentence to be negative. The clustered text is then divided into three categories. The first category is what work is done, which is a collection of past tense sentences. Second category is what work will be done, which is a collection of future tense sentences. The third category is issue, which is a collection of past tense sentences which is also a negative sentence. Finally, when we made a report all speakers which consider these three categories.

![alt text](/images/4.png)


### References
-----
* https://pypi.org/projec/moviepy/
* https://medium.com/behavioral-signals-ai/intro-to-audio-analysis-recognizing-sounds-using-machine-learning-20fd646a0ec5
* https://hackernoon.com/audio-handling-basics-how-to-process-audio-files-using-python-cli-jo283u3y
* https://pypi.orga/
* https://pypi.org/project/SpeechRecognition/
* https://pypi.org/project/pydub/
* https://www.scipy.org/docs.html
