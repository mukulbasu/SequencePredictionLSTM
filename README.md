# SequencePredictionLSTM
Predicting a sequence with LSTM

# How to use
* Prediction and testing: Use SequenceGenerationPredict.ipynb. There is also a sample graph that is generated to view the result.
* Generating Sequence data for training and validation: Use the SequenceGenerate.ipynb
* Training with the Sequence data: Use SequenceGenerationTrain.ipynb

# Parameters to play around with
* Arch: lstm or gru or both. Use the ARCHS = ["lstm", "gru"] to configure
* DATAPOINTS = 32*2000 #Controls the number of rows of datasets to be generated (For some reason, this needs to be a multiple of 32)
* MAX_NUM_FRAMES_PER_POSE = 50 #This is the number of frames for which user might hold one pose. Like a pose hold of 1 sec can result in 10 frames of one pose
* NUM_POSES = 7
* REP = [0, 1, 2, 3, 4, 5, 6, 2, 1, 0]
* MAX_SEQ_SIZE = 32*20 #Since sequence size for which data needs to be generated
* inputs # Format: 3D array: Row index, Column, (0 index for input, 1 index for total number of poses in sequence)
* targets # Format: 3D array: Row index, Column

# Important note
In keras, when training LSTM, a batch input size is necessary to be specified. Unfortunately, it expects the same batch size during prediction too.
As a workaround, you will see 2 models being defined in the code: training model (created with a batch size of the sequence size) and prediction model (created with a batch size of 1).
Lastly, post training the weights are transferred from training to prediction model by saving to a file and reloading it.
