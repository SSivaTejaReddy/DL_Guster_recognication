#Gesture Recognition – Deep learning

##Problem Statement:

We need to develop a cool feature in the smart-TV that can recognize five different gestures performed by the user which will help users control the TV without using a remote.
The following table consists of the experiments done to build a model to predict the gestures from the given data set.

You can draw inspiration from the concepts taught in the Industry demo in CNNs to experiment with the data and different architectures.
Experiment Number	Model	Result 	Decision + Explanation
1	Base Conv3D	Train_Acc : 0.95
Val_Acc: 0.26	Model is clearly  over fitting  moving to next model by reducing number of frames to 20 and image size to 120*120 and batch size = 20
2	Conv3D Model_2
	Train_Acc : 0.62
Val_Acc: 0.18	Still over fitting, as well as the model training accuracy reduced as compare to base model

Increasing Dropout % to 0.4 from 0.2 and increasing image size back to 160*160.

3	Conv3D Model_3
	Train_Acc : 0.88
Val_Acc: 0.38	Model is still Over fitting.
Increasing number of neurons in Dense layer and also applying explicit LR instead of default LR
4	Conv3D Model_4	Train_Acc : 0.63
Val_Acc: 0.58	Seen improvement but sill the accuracy can improve with good fit. Next trying ConvLSTM to see if we get better results
5	Conv2D RNN + LSTM Model_5
	Train_Acc : 0.87
Val_Acc: 0.50	Model is over fitting, next trying increase with the increase in image resolution and number of epochs
6	Conv2D RNN + LSTM Model_6	Train_Acc : 0.86
Val_Acc: 0.79	Model validation accuracy is improved as compare to previous model, But next trying increase GRU to future improve the validation accuracy.
7	Conv2D RNN + GRU Model_7	Train_Acc : 0.94
Val_Acc: 0.83	In this model we are getting good Training accuracy but not the good validation accuracy.
Increased dropout % it was slightly over fitting in the previous GRU model
8	Conv2D RNN + GRU Model_8	Train_Acc : 0.98
Val_Acc: 0.79	In this model we are getting good Training accuracy but not the good validation accuracy.
Validation accuracy need to improve.
9	Conv2D RNN + GRU Model_9	Train_Acc : 0.94
Val_Acc: 0.73	Model is still over fitting, as compared to previous model categorical accuracy is reduced.
10	GRU + Mobile Net Model_1
	Train_Acc : 0.98
Val_Acc: 0.95		

Conclusion:

The Model built with Time distributed Conv2D and ConvLSTM2D gave better results compared to all the other Conv3D models and also the model has very least number of parameters compared to other models.
As per the above experiment we have decided to go with CNN-RNN Transferred Learning (GRU) model because it gives the best accuracy as compared to any other model that have been trained.
