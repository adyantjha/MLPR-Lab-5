# MLPR-Lab-5

Aim

The aim of this project is to detect human faces in a group image and group them into similar categories using an unsupervised machine learning algorithm. After clustering the detected faces, a separate template face image is analyzed and classified into the most similar group based on its color characteristics.

Methodology

Face Detection:
The group image is first read using OpenCV and converted to grayscale.
A Haar Cascade Classifier is then applied to detect faces in the image.
Bounding boxes are drawn around each detected face.

Feature Extraction:
Each detected face is converted from BGR color space to HSV color space. From the face region, two numerical features are extracted:
Mean Hue (represents color tone),
Mean Saturation (represents color intensity)

Clustering using K-Means:
K-Means clustering (K = 2) is applied to the extracted features. The algorithm groups faces that have similar hue and saturation values and computes centroids representing the average color characteristics of each group. Each detected face is assigned to the nearest centroid.

Template Face Classification:
A separate template image is processed using the same steps:
Face detection,
HSV conversion,
Hue and saturation feature extraction.
The extracted feature vector is given to the trained K-Means model.The algorithm assigns the template face to the nearest cluster centroid and the face is plotted in the same feature space.

Key Findings

Faces taken in the same environment formed compact clusters in the feature space.
K-Means grouped faces based on color similarity rather than identity.
The template face was successfully assigned to a cluster by comparing its distance to the centroids.
However, the template face appeared far from the classroom faces in the graph because it was captured under different lighting and camera conditions.
This shows that image features such as hue and saturation are strongly affected by illumination and image acquisition settings.

Conclusion

This lab demonstrates key computer vision and machine learning techniques: face detection, feature extraction, clustering, and classification.
The clustering algorithm was able to group faces with similar color characteristics and classify a new unseen face using the nearest centroid. However, the position of the template face in the feature space was significantly different from the classroom faces due to differences in lighting and image capture conditions.
The results show that K-Means performs similarity-based classification and depends on the distribution of the training data. When a new image comes from a different environment, the algorithm still assigns a class, but the similarity is based on numerical features rather than actual person identity.
