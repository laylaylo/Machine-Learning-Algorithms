## Q1 - Support Vector Machine


### Histogram of Gradients Parameter Selection
After searching on web, we decided to use below values for the HOG features (orientations, peixels_per_cell, cells_per_block etc.). The paper of Navneet Dalal and Bill Triggs, https://hal.inria.fr/inria-00548512/document, was referenced for the parameter selection.

![output_4_1](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/e47cf481-9d99-4b3e-bafe-43b40cd32093)
    
### Q1.a(i) - binary classification problem

    2 class problem with linear kernel: accuracy: 1.0, error count: 0


### Q1.a(ii) - 15 class classification problem

    15 class problem with linear kernel: accuracy: 1.0, error count: 0


### Q1.a(iii) - Compare (i) and (ii)

In the 2 class classification problem, the SVM only needs to differentiate between two classes, whereas in the 15 class classification problem, it needs to differentiate between 15 different classes. This makes the 15 class classification problem more complex and potentially more difficult. However, the test accuracies for both problems are the same at 1. This makes it difficult to compare their classification performance, but we can observe that the computation time for the binary classification problem is significantly less.

### Q1.b


    2 class problem with hard margin linear kernel: accuracy: 1.0, error count: 0
    2 class problem with soft margin linear kernel: accuracy: 1.0, error count: 0
    2 class problem with hard margin polynomial kernel: accuracy: 1.0, error count: 0
    2 class problem with soft margin polynomial kernel: accuracy: 1.0, error count: 0
    2 class problem with hard margin rbf kernel: accuracy: 1.0, error count: 0
    2 class problem with soft margin rbf kernel: accuracy: 1.0, error count: 0
    2 class problem with hard margin sigmoid kernel: accuracy: 1.0, error count: 0
    2 class problem with soft margin sigmoid kernel: accuracy: 1.0, error count: 0


    15 class problem with hard margin linear kernel: accuracy: 1.0, error count: 0
    15 class problem with soft margin linear kernel: accuracy: 1.0, error count: 0
    15 class problem with hard margin polynomial kernel: accuracy: 1.0, error count: 0
    15 class problem with soft margin polynomial kernel: accuracy: 1.0, error count: 0
    15 class problem with hard margin rbf kernel: accuracy: 1.0, error count: 0
    15 class problem with soft margin rbf kernel: accuracy: 1.0, error count: 0
    15 class problem with hard margin sigmoid kernel: accuracy: 0.964, error count: 36
    15 class problem with soft margin sigmoid kernel: accuracy: 1.0, error count: 0


### Q1.c

We observed a notable improvement in execution time after applying PCA. This improvement can be attributed to the reduction in the number of features from 1568 to 100. Without PCA, the binary class problem took 0.5 seconds, while the multiclass problem took 15.2 seconds. However, with PCA, the binary class problem required less than 0.1 seconds, and the multiclass problem took 1.5 seconds.

    2 class problem with soft margin linear kernel after PCA: accuracy: 1.0, error count: 0

    15 class problem with soft margin linear kernel after PCA: accuracy: 0.999, error count: 1


## Q2 - k-Means Clustering and Gaussian Mixture Models
### Q2.a - Create dataset from Gaussian Mixture
##### Describe how the sampling strategy you will use work.
1. Choose one of the Gaussian distributions in the mixture according to the mixing probabilities. This can be done by generating a random number between 0 and 1 and comparing it to the cumulative distribution function of the mixing probabilities. --> ```np.random.choice(4, p=pi)```
2. Generate a sample from the chosen Gaussian distribution using its mean and covariance. Since we consider 2-dimensional Gaussians, there are two variables. Therefore, use the ```multivariate_normal function``` from the numpy.random module. This function takes the mean vector and covariance matrix as inputs and returns a sample from the corresponding Gaussian distribution.
3. Repeat steps 1 and 2 to generate as many samples as desired.

![output_24_0](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/7d7a40c4-06ac-4295-a312-a59a27982056)

### Q2.a - Implement the k-means algorithm from scratch.
    
![output_27_0](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/6101e07b-7e40-41e6-99b4-919aa7bb6d8d)

#### Is the k-means able to correctly cluster the different components of the mixture?
The K-means algorithm failed to accurately cluster the different components of the mixture, as evident from the comparison of the two graphs above. The main reason behind this failure was the significant overlap between the clusters, which posed a challenge for K-means to distinguish and separate them correctly. Although the algorithm can also struggle with other factors such as varying cluster sizes and densities, this was not the case in our scenario, as our clusters were generated with identical sigma values, resulting in clusters of similar sizes and densities.

means of Mixed Gaussian Model : μ1 =(0,1), μ2 =(1,0), μ3 =(−1,0), μ4 =(0,−1)
centroids:

    [[-0.56966631  1.09889189]
     [-1.37796911 -0.53352147]
     [ 0.67346774 -1.07927873]
     [ 1.25523694  0.9915144 ]]
     
    Accuracy of KMeans: 0.118

