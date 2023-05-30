# Lab 6

## Part A: "Master" instance

I chose AWS in this lab.
### Steps:
1. I launched an EC2 instance in AWS with the smallest instance type(t2.micro)

![](./images/launch_instance1.png)
![](./images/launch_instance2.png)
![](./images/launch_instance3.png)

2. & 3. connecting to the instance, installing appache

![](./images/it_works.png)

4. creating default page

![](./images/hello_lab6.png)

5. an image created successfully

## Part B: "Master" instance

### Steps:

6. launching 3 instances from the copy

![](./images/launch_3instances.png)

7. done
8. done
![](./images/hello_instance1.png)
![](./images/hello_instance2.png)
![](./images/hello_instance3.png)
9. done
![](./images/load_balancer1.png)
![](./images/load_balancer2.png)
10. If I access ![this](http://lab6-895946187.us-west-2.elb.amazonaws.com) address, I see different html pages(each instance has its unique index.html page).

![](./images/hello_load_balancer1.png)
![](./images/hello_load_balancer2.png)

11. done
![](./images/log_lab1.png)
![](./images/log_lab2.png)
![](./images/log_lab3.png)
12. after changing the algorithm to Least outstanding requests
![](./images/change_algorithm.png)



## Part C: "Master" instance

I used Locust
I stopped the test after couple of seconds

13. creating load test
![](./images/locust.png)
![](./images/locust_statistics.png)


14.  
logs after running locust
![](./images/log2_lab1.png)
![](./images/log2_lab2.png)
![](./images/log2_lab3.png)

chart of locust
![](./charts.png)


