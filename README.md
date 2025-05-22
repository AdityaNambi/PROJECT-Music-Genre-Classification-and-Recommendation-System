# PROJECT-Music-Genre-Classification-and-Recommendation-System
This project classifies music genres using MFCC features and a CNN model trained on the GTZAN dataset. It also recommends similar tracks using cosine similarity. Additional features include genre prediction and spectrogram visualization, combining audio processing and deep learning effectively.


1. Feature Extraction
The extract_features function loads an audio file and extracts its MFCC (Mel-Frequency Cepstral Coefficients), which summarize the timbral and spectral aspects of sound. The average of the MFCCs over time is returned as a compact feature vector.

2. Loading the Dataset
The dataset directory is scanned for audio files under each genre. For every file, the MFCC features are extracted and stored along with the genre label and filename. Any files that cause errors are safely skipped.

3. Preprocessing
The feature vectors are converted into a NumPy array, and genre labels are encoded using LabelEncoder. These are further converted into one-hot encoded format. The data is then split into training and validation sets for model evaluation.

4. Building the CNN Model
A deep learning model is constructed using the Sequential API of Keras. It uses convolutional layers to capture local patterns in the MFCC vectors, pooling layers to reduce dimensionality, and dropout to prevent overfitting. The model ends with a softmax layer for multi-class classification.

5. Training the Model
The model is compiled and trained for 50 epochs using the Adam optimizer. Training and validation accuracy are monitored using the fit function. The features are reshaped to match the input shape expected by the CNN.

6. Evaluation and Plotting
Once trained, the model's performance is evaluated on the validation set. A graph showing training vs. validation accuracy over epochs is plotted to visualize learning trends and ensure the model is not overfitting.

7. Preparing Data for Recommendation
All feature vectors and metadata (genre and filename) are stored in a DataFrame. This allows for future use in similarity-based recommendations using cosine similarity.

8. Genre Prediction
The predict_genre function accepts a file path, extracts its features, and predicts the most probable genre using the trained model. It also provides a confidence score to indicate prediction certainty.

9. Music Recommendation
The recommend_similar function finds the most similar tracks by comparing feature vectors using cosine similarity. It returns the top 5 recommended tracks based on their proximity to the input file in feature space.

10. Visualizing Spectrogram
The show_spectrogram function generates and displays a Mel spectrogram of the audio file, offering a visual insight into its frequency content and dynamics over time.

11. Example Usage
This block demonstrates how to use the system: it performs genre prediction on a jazz track, shows top recommendations, and plots its spectrogram for analysis.
