## Motivation

![equation1](https://latex.codecogs.com/gif.latex?\begin{center}&space;\begin{eqnarray*}&space;min\&space;f(x)\&space;&&space;&st\&space;x\&space;\in&space;\&space;D&space;\\&space;&&space;&\text{&space;where&space;D&space;,&space;f&space;are&space;convex}&space;\end{eqnarray*}\end{center})
We have many tools to solve minimization problems, such as gradient descent.
under stress, it requires additive factors, to be optimal, we can think of using lagrange or the projection gradient.
The projection gradient is to project at each iteration the update x in the descent of the gradient.
To be free of projectionection; there is conditional gradient method where update is solved directly over the
constraint set D.

In the Frank-Wolfe Algorithm, Instead of taking the opposite of gradient as usually used in gradient descent,![equation2](https://latex.codecogs.com/gif.latex?\begin{center}&space;$$x_{t&plus;1}&space;=&space;x_t&space;-&space;\gamma&space;_t&space;\nabla&space;f(x_t)&space;$$&space;\end{center})we look for a vector which is much on the opposite direction with gradient. 

![equation3](https://latex.codecogs.com/png.latex?\fn_jvn&space;\begin{center}&space;$$&space;{\displaystyle&space;s_t&space;\in&space;argmin&space;_{s\in&space;D}&space;<&space;{\nabla&space;}&space;f\(x_t\),&space;s&space;>&space;\)}&space;\text{&space;And&space;update&space;}&space;\\&space;\begin{eqnarray*}&space;x_{t&plus;1}&space;&=&&space;x_{t}&space;&plus;&space;\gamma&space;_t&space;(s_t&space;-&space;x_{t}&space;)\\&space;&=&(1-\gamma&space;_t)&space;x_{t}&space;&plus;&space;\gamma&space;_t&space;s_t&space;\end{eqnarray*}&space;$$&space;\end{center})


The default choice for step sizes is ![equation4](https://latex.codecogs.com/png.latex?\fn_jvn&space;$\gamma_t&space;=&space;2/(t&space;&plus;&space;1),\&space;t&space;=&space;1,&space;2,&space;\dots&space;$)  and with any choice of ![equation5](https://latex.codecogs.com/png.latex?\fn_jvn&space;$\gamma_t&space;\in&space;[0,&space;1],&space;x_t&space;\in&space;D$) by the convexity of D.
![equation6](https://latex.codecogs.com/png.latex?\fn_jvn&space;$\\&space;\textbf{Recall}&space;:&space;\\&space;{\displaystyle&space;<&space;\mathbf&space;{a}&space;,&space;\mathbf&space;{b}>&space;=\|\mathbf&space;{a}&space;\|\&space;\|\mathbf&space;{b}&space;\|\cos(\theta&space;)}\\&space;\text{&space;so&space;minimize&space;}&space;{\displaystyle&space;<&space;\mathbf&space;{a}&space;,&space;\mathbf&space;{b}>&space;}&space;\text{&space;involved&space;}&space;\cos(\theta)&space;$)
to be close to -1 which means the angle between a and b to be   ![equation7](https://latex.codecogs.com/png.latex?\fn_jvn&space;$\pi&space;\&space;or&space;\&space;{\pi&space;&plus;&space;2k\pi}&space;\text{&space;with&space;k&space;}&space;\in&space;\mathbb{Z}$)
 
 


For the ![equation8](https://latex.codecogs.com/png.latex?\fn_jvn&space;$\mathcal{l}_1$) regularized problem
![equation9](https://latex.codecogs.com/png.latex?\fn_jvn&space;$${\displaystyle&space;\min&space;_{x}&space;\&space;f(x)&space;\\&space;\text{&space;subject&space;to&space;}&space;\|&space;x&space;\|_1&space;\leq&space;t&space;}$$)
![equation10](https://latex.codecogs.com/png.latex?\fn_jvn&space;$&space;D&space;=&space;\{S:&space;\|&space;S&space;\|_1&space;\leq&space;t&space;\}$)
with Condition gradient ![equation11](https://latex.codecogs.com/png.latex?\fn_jvn&space;$&space;s_t&space;\in&space;argmin&space;_{s\in&space;D}&space;<&space;{\nabla&space;}&space;f(x_t),&space;S&space;>&space;$)

With a change of variable , S = ts.

![equation12](https://latex.codecogs.com/png.latex?\fn_jvn&space;$\begin{eqnarray*}&space;{\displaystyle&space;argmin_{s\in&space;D}&space;<&space;{\nabla&space;}&space;f(x_t),&space;S&space;>&space;}&space;&=&&space;{\displaystyle&space;argmin&space;_{S\leq&space;t}&space;<&space;{\nabla&space;}&space;f(x_t),&space;s&space;>&space;}&space;\\&space;&&space;=&&space;{\displaystyle&space;t\&space;argmin&space;_{s\leq&space;1}&space;<&space;{\nabla&space;}&space;f(x_t),&space;s&space;>&space;}&space;\\&space;&&space;=&space;&&space;{\displaystyle&space;-&space;t\&space;argmax&space;_{s\leq&space;1}&space;<&space;{\nabla&space;}&space;f(x_t),&space;s&space;>&space;}&space;\end{eqnarray*}$)




<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\fn_jvn&space;$argmax&space;_{s\leq&space;1}<{\nabla&space;}&space;f(x_t),&space;s&space;>&space;=&space;\partial&space;\|\nabla&space;f(x_{t-1}\|_\infty&space;\\&space;\text{&space;So&space;we&space;have&space;}&space;s_{t-1}&space;\in&space;-&space;t&space;\cdot\partial\|\nabla&space;f(x_{t-1})\|_\infty&space;.$" target="_blank"><img src="https://latex.codecogs.com/png.latex?\inline&space;\fn_jvn&space;$argmax&space;_{s\leq&space;1}<{\nabla&space;}&space;f(x_t),&space;s&space;>&space;=&space;\partial&space;\|\nabla&space;f(x_{t-1}\|_\infty&space;\\&space;\text{&space;So&space;we&space;have&space;}&space;s_{t-1}&space;\in&space;-&space;t&space;\cdot\partial\|\nabla&space;f(x_{t-1})\|_\infty&space;.$" title="$argmax _{s\leq 1}<{\nabla } f(x_t), s > = \partial \|\nabla f(x_{t-1}\|_\infty \\ \text{ So we have } s_{t-1} \in - t \cdot\partial\|\nabla f(x_{t-1})\|_\infty .$" /></a>
<br/>
Therefore Frank-Wolfe update is thus ![equation13](https://latex.codecogs.com/png.latex?\fn_jvn&space;i_{t-1}&space;\in&space;argmax&space;\nabla&space;_i&space;f(x_{t-1}&space;)&space;\\&space;i=1,...p)
![equation 14](https://latex.codecogs.com/png.latex?\fn_jvn&space;$$x_t&space;=(&space;1&space;-&space;\gamma&space;_t&space;)x_{t-1}&space;-&space;\gamma&space;_t&space;\cdot&space;\&space;sign&space;\nabla_{i_{t-1}}&space;f(x_{t-1}&space;)&space;\cdot&space;e_{i_{t-1}}$$&space;,&space;\text{&space;so&space;}&space;\\&space;\\&space;$s_t&space;=&space;sign&space;\&space;\nabla_{i_{t-1}}&space;f(x_{t-1}&space;)&space;\cdot&space;e_{i_{t-1}}&space;\text{&space;where&space;}&space;e_i&space;=&space;(0,\cdots,&space;1,&space;\cdots&space;)$,) 1 at i-th position  



