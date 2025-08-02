### **Music Genre Clustering Project**

### **1. Introduction**

This project aims to use unsupervised machine learning to group songs from a Spotify dataset into distinct clusters based on their musical characteristics. The goal is to discover new, data-driven "music segments" that may not align with traditional genre classifications. By analyzing the features of each cluster, we can gain a deeper understanding of the relationships between different musical attributes.

### **2. Data and Features**

The project utilizes the `Spotify-2000.csv` dataset, which contains 1994 songs and their associated metadata and audio features. The key features used for this analysis are:

* **Beats Per Minute (BPM):** The tempo of the song.
* **Loudness (dB):** The overall loudness of the song.
* **Liveness:** A measure of the presence of an audience in the recording.
* **Valence:** A measure of the musical positivity conveyed by a track (e.g., happy, cheerful, euphoric).
* **Acousticness:** A confidence measure of whether the track is acoustic.
* **Speechiness:** A measure of the presence of spoken words in the track.

### **3. Methodology**

1.  **Initial Data Exploration:** An initial correlation analysis was performed on the numerical features. This step provided early insights into the relationships between features, such as the strong positive correlation between `Energy` and `Loudness (dB)` (0.73), and the strong negative correlation between `Acousticness` and `Energy` (-0.66). This confirmed that songs with higher energy tend to be louder and less acoustic.

2.  **Feature Selection and Preprocessing:**
    * The six features listed above were selected for clustering.
    * To ensure all features contributed equally to the clustering process, the data was scaled using `MinMaxScaler`. This is a critical step for distance-based algorithms like K-Means.

3.  **Clustering:**
    * The **K-Means clustering algorithm** was applied to the scaled data.
    * The model was configured to create **10 distinct clusters**, or "music segments."

### **4. Key Findings and Insights**

The clustering successfully partitioned the dataset into 10 groups. By examining the average feature values of each cluster (the cluster profiles), we can characterize the unique musical identity of each segment.

* **Cluster 2 (Acoustic/Slow):** This cluster is defined by the lowest average `Beats Per Minute (BPM)` (93) and the highest average `Acousticness` (81), suggesting it contains predominantly slower, more unplugged or acoustic-heavy songs.

* **Cluster 3 (Upbeat/Happy):** This segment stands out with the highest average `Valence` (84), indicating that it is a collection of songs that are generally perceived as happy and cheerful.

* **Cluster 4 (Live Recordings):** This is a small but highly distinct cluster, with an exceptionally high average `Liveness` score (76). This strongly suggests that this cluster successfully isolated live performance recordings from the rest of the dataset.

* **Genre Distribution:**
    * The largest clusters (e.g., Cluster 5 and Cluster 3) showed a heavy concentration of the `album rock` genre. This highlights that `album rock` is a broad genre and its songs have a variety of musical attributes, leading them to be distributed across different clusters.
    * Conversely, the more distinct clusters, like the "Live Recordings" cluster, contained a wider variety of genres. This indicates that the clustering was successful at identifying songs based on their shared musical properties rather than their traditional genre labels.

### **5. Visualization**

A 3D scatter plot of `Beats Per Minute (BPM)`, `Energy`, and `Danceability` was created to visualize the cluster separation.

* **Separation:** The plot confirmed that some clusters are indeed well-separated based on these three features, which validates the effectiveness of the clustering algorithm in grouping songs with similar characteristics.
* **Overlap:** The visualization also revealed a significant overlap among other clusters, suggesting that for many songs, the differences between clusters are more subtle and defined by the other features used in the clustering process (e.g., `Loudness (dB)`, `Liveness`, `Acousticness`, and `Speechiness`).

### **6. Next Steps**

1.  **Dimensionality Reduction:** Use a technique like Principal Component Analysis (PCA) to visualize the clusters in a 2D plot, which can often be easier to interpret.
2.  **Refined Clustering:** Experiment with different numbers of clusters or explore other clustering algorithms (e.g., DBSCAN) to see if they yield more insightful groupings.
3.  **Further Analysis:** Dive deeper into specific clusters to identify the top songs, artists, or genres within each segment to better understand its cultural and musical context.
