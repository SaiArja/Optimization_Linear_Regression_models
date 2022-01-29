# Optimization_Linear_Regression_models
In this Repo I have implemented some of the optimization algorithms used in the Linear Regression with nice plots and explination

The main challange of the Linear Regression is to minimise the cost function. that is to find the parameters that are well sutable to minimise the cost function

the Treditional mathematical way of solving this problem is with Normal Equaltion

Normal Equation

i have the below data points


![image](https://user-images.githubusercontent.com/76277751/151663279-1abaa65c-2746-4e8d-815a-0cacb35bc3e0.png)


i will find the theta best with the treditional solution that is normal equation


![image](https://user-images.githubusercontent.com/76277751/151663328-5630d902-51a4-4a70-881a-5975db41e7d7.png)


i got the theta_best as array([[4.15834119], [2.87662956]])

and the regression line as 


![image](https://user-images.githubusercontent.com/76277751/151663370-2bc5bf4f-9fa5-4c48-b2ac-a2fb1c7a0313.png)



Above is the soolution with the Normal equation which looks good, but the issue with normal equation is that we have to use inv() from numpy module, it will work fast if data is small but as the features increse the completxity increses thus lead to slowness of the algorithm

one of the solutions to above problem is to use Scikit-learn Linear Regression which will use "scipy.linalg.lstsq()" which is "least squares"

which uses the Singular value decomposition(SVD) and computes the Sudo-inverse of the function that is 𝜃=𝑋+𝑦

Refer https://stackoverflow.com/questions/49357417/why-is-numpy-linalg-pinv-preferred-over-numpy-linalg-inv-for-creating-invers

the advantage of the Linear Regression from scikit-learn is that we will get the intercept and coef values directly

for the above example we got array([[2.87662956]]), array([4.15834119]))



![image](https://user-images.githubusercontent.com/76277751/151663567-7f66f34c-053b-4fe0-a36e-c0d4d700d4e7.png)


which is almost all same but little fast.

the next one is one of the popular algorithem **Gradient Descent**



![image](https://user-images.githubusercontent.com/76277751/151663667-b047c9ca-4afd-4bb9-9b8a-25fed915d4cf.png)


and the update happens with below formula 



![image](https://user-images.githubusercontent.com/76277751/151663688-8480ee1e-6e3d-4769-b334-4f3ce59c006a.png)



here the alpha (i have used that as eta in my notebook) is a hyper parameter and called as learning rate

when the learning rate is too low, the algorithem reaches minimum but it will take long time.

here for the above data i have taken the alpha as 0.05 then my GD looks as below



![image](https://user-images.githubusercontent.com/76277751/151663815-4f7ec649-7478-4462-891a-eec6cb8a97ad.png)



and the regression line looks as below



![image](https://user-images.githubusercontent.com/76277751/151663856-7c50fecf-7511-4c4b-a436-73ec8e9579df.png)



you will be understanding the significance of the graphs after seeing the graphs for the optimum alpha value

i have taken the alpha as 0.1 and the graphs as below



![image](https://user-images.githubusercontent.com/76277751/151663893-ecc7e670-b93d-41ae-b278-9c980ac18597.png)



you can see that in this plot GD reaches the minimum at a less steps thus takes less time



![image](https://user-images.githubusercontent.com/76277751/151663925-2bb4d5b6-0e53-405a-8548-21a5c68276b5.png)



when the learning rate is too high the algorithm jumps away and away each step from the solutions 



![image](https://user-images.githubusercontent.com/76277751/151663977-044f2a42-9748-4768-8b02-07627697b738.png)




![image](https://user-images.githubusercontent.com/76277751/151663985-b8adaac6-2fb6-465d-8c1c-45033993bf86.png)




the Gradient descent or batch gradient descent uses whole data for every iteration which will make this slow when training set is too large. to overcome this we have **Stochastic Gradient Descent**

The word ‘stochastic‘ means a system or a process that is linked with a random probability. Hence, in Stochastic Gradient Descent, a few samples are selected randomly instead of the whole data set for each iteration




![image](https://user-images.githubusercontent.com/76277751/151664156-4f9117d1-5523-4746-a2fa-2177cbe7b6ad.png)



this SGD is not regular like normal GD it is very irregular as it is taking one different instance at a time. this helps in cover coming the local minima problem for the cost function other then MSE. but it can not be stable at the global minima also it keeps jumping around the global minima. lets see that in the below plot for the data taken



![image](https://user-images.githubusercontent.com/76277751/151664257-49c74e8b-0542-4c0b-9324-ba569a73809b.png)




the theta values are array([[4.24354547],[2.86180106]])

we can see that this keeps playing around 4.2 and 2.8 

so this is not exactly minima points but points very near to that. 

thats why we will be saying that the **values are good but not optimal**

you can observe one more thing that within very less steps it reaches the points near to the global minima

lets see the fiting lines



![image](https://user-images.githubusercontent.com/76277751/151664348-9954bf2e-5d9d-4ff2-ba86-9b67ee5eb306.png)



and the best fit line as below



![image](https://user-images.githubusercontent.com/76277751/151664380-fd04c4a0-f557-4eb2-8692-7fb5d8992d27.png)



