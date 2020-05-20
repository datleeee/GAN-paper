# GAN
## 1. Introduction
GAN is a generative model, which
- Learn to create something, and improve until perfect
- Generate datas from scratch, mostly images but there are also many other applications

GANs network:
- Composed of 2 networks **Generator** and **Discriminator**
- **Generator**: try to generate real data
- **Discriminator**: try to recognize which datas are generated from **Generator** and which are real.

Goal of GAN:
* Generated data to a very 'real' level so that Discriminator can't distinguish which are real data, which are generated ones.

Examples:

![](https://i1.wp.com/nttuan8.com/wp-content/uploads/2019/11/1-1.png?resize=768%2C510&ssl=1)

Real money = real data 
Fake money = data generated from Generator

Training process of GAN:
* Police (Discriminator): 
    * Keep learning to distinguish which money are real/fake
    * Keep telling the counterfeiter (Generator) that his money is still fake and need to be improved to be more 'real' next time
* Counterfeiter: 
    * Keep taking feedback from polices and learn to prints fake money that is more 'real'
* The process ends when the counterfeiter print fake money that polices can't distinguish anymore

## 2. Generator and Discriminator 
We will describe these in the case of GAN for creating images
### Generator (G)
* Take some noise **z** as input, using normal/uniform distribution
* **z** as input, use generator G to create image x(x=G(**z**))

![](https://miro.medium.com/max/1400/1*8TTaFyyh_WyKWE--H-Pl0A.jpeg)

### Discriminator (D)
* Learn what features make image real (by training with real images and generated images seperately)
* Provide feedback to the generator --> create a better, more realistic image


![](https://miro.medium.com/max/1400/1*9qW0I-2M6qKGBwifhnPKPQ.png)

* The output D(X): probability that the input x (generated data from Generator G) is real
* If D(X) = 1, then the input x is real.
* If D(X) = 0, then the input x is generated

![](https://miro.medium.com/max/1400/1*_uFUaxXIEjCDm_UTzbyleA.png)

* Throgh this process, the discriminator identifies **features** that contribute to real image
* Train back the Generator by **Backpropagation**

![](https://miro.medium.com/max/1400/1*roO-E4KTolB-wttrs-u16g.jpeg)

## 3. Adversarial nets
* Idea of Backpropagation
* Discriminator outputs a value D(x) indicating the chance that x is a real image. 
* Our objective = maximize the chance to recognize real images as real and generated images as fake (the maximum likelihood of the observed data). 
* Cross-entropy (measure the loss): p log(q). 
* For real image, p (true label for real images) = 1. 
* For generated images, reverse the label. So the objective becomes:

![](https://miro.medium.com/max/1400/1*4xAHMaUGXeOQnNJhzjq-4Q.jpeg)

* On the generator side, its objective function wants the model to generate images with the highest possible value of D(x) to fool the discriminator.

![](https://miro.medium.com/max/1400/1*n235XEigXKL3ktL08d-CZA.jpeg)

* Its a minimax game, these 2 models are fighting over 1 number (error rate).
* One of them want the number to be high, ones wants to be low. 
* **Error rate**: discriminator wants *low error rate* (maximize V), generator wants *high error rate* (minimize V)

![](https://miro.medium.com/max/1400/1*ihK3whUAZ_0UeK4SJicYFw.png)

## 4. Theoretical Results
The pseudo-code below puts everything together and shows how GAN is trained.

![](https://miro.medium.com/max/1400/1*hlFyF-klXQunFpmoeA89jQ.png)




















































