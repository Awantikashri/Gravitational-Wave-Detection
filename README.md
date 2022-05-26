<h2 style="text-align:center;">Data Mining and Analysis Project ( 2021 )</h2>

***

## Contents of this Notebok
1. Imports
2. Reading DataSet
3. Explorative Data Analysis
4. Preprocessing
5. Model Training
6. Evaluation
7. Results and Conclusion

***
***Kaggle Challange Name:*** [G2Net Gravitational Wave Detection](https://www.kaggle.com/c/g2net-gravitational-wave-detection) - (Submission Deadline : 30th September, 2021)
***
***Introduction*** : 
*Gravitational Waves have been discussed since the beginning of the 20th century, and scientifically researched since the Einstein's General Theory of Relativity. They are caused by massive celestial bodies, like the Neutron Stars or **Black Holes**, when they accelerate they cause gravitational waves, in the form of waves, propagating through the curvature of space-time at the speed of light. These disturbances can be felt on the other side of the observable universe, but are extremely weak as they lose energy as gravitational radiation. It can be imagined similar to throwing a pebble in the pond, the site where the pebble hits water is the source of the disturbance and the outgoing ripples, are the gravitational waves, that get weaker as they move away from the source.In February 2015, the Laser Interferometer Gravitational-wave Observatory **(LIGO) Scientific Collaboration and the Virgo Collaboration** announced the first observation of a Gravitational-Wave (GW) signal from a **stellar-mass Compact Binary Coalescence (CBC) system** .Despite all the initial successes, the future of GW astronomy is facing many challenges. Because of the effectiveness of ML algorithms in identifying patterns in data, ML techniques may be harnessed to make all these searches more sensitive and robust. Applications of ML algorithms to GW searches range from building automated data analysis methods for low-latency pipelines to distinguishing terrestrial noise from astrophysical signals and improving the reach of searches.*


![KLE TU](https://media2.giphy.com/media/xT9IgoYWAh5lYliiYM/giphy.gif)


***Problem Statement*** : *To preprocess data then build, train & evaluate binary classification model to predict if the given set of signals has Gravitational Waves in them or not.*

***Objectives :*** 
1. *To understand and visulaize raw data using EDA methods*
2. *To build and train model using Deep Learning Techniques*
3. *To evaluate model using metrics like ROC AUC (receiver operating charateristics area under curve)*

***
Note: This notebook was developed and run in the kaggle notebook environment.

***Modeling***
**Strategy**

- This is essentially a signal processing problem with classification task, there can be two ways in which we can build models around this data, as also mentioned in the [LIGO research paper](https://arxiv.org/pdf/1908.11170.pdf) - using "raw" signals with minimal pre-processing and using "images" by transforming the waves into spectrograms. 
- However, building models on raw signal data, by following the cleaning steps from respective publications, didnot yield acceptable results. It is worth mentioning that only a part of the data was used while strategy selection process, and it was concluded that more pre-processing was necessary, or rather proper pre-processing, if we were to use raw signal.
- Eventually, the second method that we went with in this project, is used to transform the waves into the spectrogram image. We train two models to evaluate the results:
1. Simple CNN- a simple CNN architecture that is a modified version of the model usually used in MNIST Digit Recognizer tutorials. This acts as our baseline model.
2. EfficientNet-a EfficientNetB7 model that has been developed and pre-trained on ImageNet dataset. This model is chosen as it is known for its excellent performance with significantly fewer number of parameters, that can drastically improve the computational efficiency.

***Results & Conclusions***

- Gravitational Waves are NOT EASY to detect! Once detected, they are hard to find. 
- After sifting through a varierty of preprocessing steps, we transformed the orginal strain wave data into frequency spectrograms, which are images that we then used to train deep learning models. 
- One of the biggest challenges in this project was managing such a large dataset, which was solved by using the TensorFlow's tf.data API, and streamlining the entire workflow all the way from data import to model training & prediction tasks. This helped us achieve the goal of this project of building a pipeline that is flexible and can be reused in the future.
- Our simple CNN architecture, just after 3 epochs, was performing more than expected.
- The Efficient Net B7 model worked quite well with AUC score of 0.8754
- We evaluated the models for ROC AUC score, as we wanted our model to be good at separating the two classes, but also tracked accuracy scores for comparison. Overall, we achieved AUC score of 0.8754 on the test dataset from kaggle. 
