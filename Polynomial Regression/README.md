# Polynomial Regression

<center>
    <img src = "https://i.imgur.com/AmFJfEn.jpg">
    <a href="https://wallpapercave.com/beautiful-road-wallpaper">Image source</a>
</center>

## Prerequisite

### Linear regression

在了解 Polynomial regression 之前，我們先看到 Linear regression，它擁有跟其相接近的特質，差別在於 Linear regression 相較來說只將輸出與單一一個輸入定義線性關係，Linear regression 所建立的模型會是一條直線，而該直線會偏向與周圍數據建立最貼近彼此的平面關係。

相對於 Linear regression，Polynomial regression 能更加容易建構出與複雜數據間的關係，但也要小心 Polynomial Regression 會產生過度擬合數據的問題 (overfitting)。

### Gradient descent

為了使模型更貼近數據，使用 Gradient descent 是一種方法。

而梯度下降法 (Gradient descent) 是拿來求出最低的損失函數 (loss function) 的參數，藉由 Gradient descent 不斷更新模型的參數，我們可以發現模型可以更加擬和原先所給定的數據集，從而使的損失函數的數值 (loss value) 越來越小。

> **What is loss function / loss value**
>
> 在透過 Regression model (Ex: Polynomial Regression)，我們希望能藉由模型去貼近原先所給定的數據，使得模型能精準去預估我們所給予的輸出相對應的輸入。
> 
> 但要能了解我們訓練模型的輸出跟實際輸出，我們會使用 loss function 來定義，其中它產生的 **loss value 便是實際數值和預測數值的差**

其中，Regression model 所常用的 loss function 包含:
1. 均方誤差 (Mean square error a.k.a MSE)

$$
    MSE = \frac{1}{n} \sum^n_{i=1}(y_i - \hat{y}_i)^2
$$

2. 平均絕對值誤差 (Mean absolute error a.k.a MAE)

$$
    MAE = \frac{1}{n} \sum^n_{i=1}|y_i - \hat{y}_i|
$$

其中 $\hat{y}$ 為模型估計的輸出，而 $y$ 為原本資料輸入所對應的輸出

3. 開根均方誤差 (Root MSE / RMSE)

$$
    RMSE = \sqrt{\frac{1}{n} \sum^n_{i=1}(y_i - \hat{y}_i)^2}
$$

為了避免均方誤差 (MSE) loss value 過大， RMSE 將其開根


>**Choose MSE or MAE ?**
>* MAE (Mean Absolute Error)：
>
>選擇它的優點在於，其損失函數對於與大多數資料相差較多的**異常值 (outlier)** 較不敏感，但也因於此 MAE 不能預測偏差，因為其損失函數只考慮絕對值得差異。
>
>* MSE (Mean Squared Error)：
>
>MSE 在是一个凸函數，容易使用梯度下降算法進行優化，因为它使用平方誤差計算資料間的差異，所以導致其損失函數對偏差的敏感。
>
>但在選擇 MAE 或 MS的同時，數據的性質和分析模型的具體要求才是選擇哪種 Loss function 放在 Regression model 的重點。


## Goal

Polynomial Regression 是一種希望透過數據使用多項式預測函數來建模，並且未知的模型參數也是通過數據來估計的回歸模型。

## Background

> 這裡的輸入可稱為自變量，輸出可稱為因變量

Polynomial Regression 期望透過輸入 $x$ 來與輸出 $y$ 的關係建立模型，其中判斷函數為 $n$ 之多項式，相較於 Linear Regression 中，$n=1$，$y = \beta_0 + \beta_1 x$，Polynomial Regression 更容易拿來用於模擬非線性變量之間的關係。

而兩者目標是確定係數的值，可以使預估出來的輸出值和實際值的差異最小化。

Polynomial Regression 的基本思想是將原始輸入來建立多項式的項，使得預測函數可以再線性回歸模型中使用，被表示为一个多項式方程

$$
    y = \beta_0 + \beta_1 x + \beta_2 x^2 + ... + \beta_n x^n
$$

其中，$x$ 為原先資料的輸入項，$y$ 為輸出項，$\beta_0$ 是 $y$ 的偏差值，$\beta_1, \beta_2, ... \beta_n$ 為多項式的係數。

Polynomial Regression 的建立模型目的是確定係數值，可以使輸出實際值和预測值之間的差異最小。

而優化過程可以用優化算法来完成，例如梯度下降或最小二乘法。

最後只要係數被確定，多項式方程就可以用来根據輸入量的新值輸出進行預測。