### Students
Kemal Cagin Sertkaya - 2019400264

Leyla Yayladere - 2018400216

Mustafa Atay - 2020400333

### Q1.a




Decision boundary occurs when $h(x) = sign(w^Tx)$ changes from positive to negative or vice versa. In other words, when $w^Tx = 0$ there is a decision boundary. Therefore, $w^Tx = 0 \Rightarrow w_0 + w_1x_1 + w_2x_2 = 0 \Rightarrow x_2 = -\frac{w_0}{w_2} - \frac{w_1}{w_2} x_1$. Therefore, $a = -\frac{w_1}{w_2}$ and $b = -\frac{w_0}{w_2}$.



### Q1.b
![output_4_0](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/637b0311-78f9-48e0-b75c-ef5c706d78ce)
    


### Q1.c


    Number of updates before converging: 11


![output_6_1](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/da9c2906-75e5-42f7-b245-e6a8b0962250)


### Q1.d

    Number of updates before converging: 498


![output_8_1](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/4297dd39-df21-466e-8b50-adbd4aaee2f0)

### Comparing Results with (c):
Comparing the results between 20-sized dataset and 1000-sized dataset, we observed that the final hypothesis g is closer to the target function f in the 1000-sized dataset.
However, the number of updates before converging is higher in the 1000-sized dataset. 
Since both datasets are separable, our perceptron learning algorithm will eventually converge. But with more data samples, this algorithm will take more step to converge. Because it has more probability to misclassify a point.
Therefore it will get closer to the target function f.


### Q2.b

We chose to use closed-form (analytical) solution of logistic regression, which is:

#### $w = (X^TX)^{-1}X^Ty$

    10000
    root mean square error for training data 0.028052551350335693
    1000
    root mean square error for test data 0.06417742008519657


### Q2.c

We chose to use Principal Component Analysis (PCA) from scikit-learn to reduce the dimensionality of the data.
We chose PCA, because it has the following advantages:[2]

- The correlated features are removed, which reduces the dimensionality of the data.
- We only select the most important features, which reduces the computational cost also.
- After we calculated the density of our training set. There is no missing or zero value and >99% of the data is not near zero. Since PCA is most popular feature selection algorithm, if the dataset is not sparse, we can use PCA to reduce the dimensionality of the data.[1]

[1]: https://machinelearningmastery.com/dimensionality-reduction-algorithms-with-python/
[2]: https://statisticsglobe.com/advantages-disadvantages-pca#advantages-of-the-pca

However, our RMSE has increased after applying PCA. This is probably because it has removed some important data. So, there is a trade-off between the computational time/cost and the accuracy of the model. 
With 4096 features in part b, it takes ~34.2 seconds with ~0.0021 RMSE in training data and 0.097 RMSE in test data. On the other hand, in part c, it takes ~16.4 seconds with ~0.2 RMSE in training data and ~0.22 RMSE in test data. Hence, we can observe that the computational time has decreased while the RMSE has increased.

    (10000, 1000)
    10000
    RMSE for training data with PCA: 0.199816724817696
    1000
    RMSE for testing data with PCA: 0.22443144783365013



### Q3.b

![output_19_0](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/f2846a5e-49ba-4c06-ab74-0279a603e287)

![output_19_1](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/69e878f5-8180-432c-aeea-0955b6c256e4)

### Q3.c
$$\text{the gradient of the logistic loss:     } \frac{1}{N}  \sum_{n=1}^{N} X^T (\mathbf{\hat{y}} - y) $$

    Train Errors: 31
    Train Accuracy: 0.9801409352978859
    Test Errors: 19
    Test Accuracy: 0.9551886792452831

![output_21_1](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/8881d2f7-145d-4c86-bb0d-61da0f6529dd)


![output_21_2](https://github.com/laylaylo/Machine-Learning-Algorithms/assets/74381463/7952d0f0-0f31-4a3f-bfa1-af8361d5e802)


### Q3.d  

    Best lambda: 0
    Train Errors: 2
    Train Accuracy: 0.9987187700192185
    Test Errors: 4
    Test Accuracy: 0.9905660377358491


##### Did regularization improve performance

In values [0, 0.003, 0.01, 0.03, 0.1, 0.3, 1, 3, 10, 30] for lambda, the best result came with labmda=0, which means no regilarization at all.

Therefore, we concluded that regularization didn't improve the accuracy. That is because, the data was not overfitting at the first place.
